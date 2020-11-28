# 8086
....model small
.stack 50
.data
    NL db 10,13,'$'
    mang db 100 dup(?)
.code
 main proc
    mov ax,@data
    mov ds,ax
    lea si,mang   ;mov si,offset mang 
    xor cx,cx     ;xoa thanh ghi cx     
    lapdoc:
    mov ah,1
    int 21h
    cmp al,13     ;so sanh voi enter
    je ketthuc
    mov [si],al    ;dia chi gian tiep thanh ghi
    inc si   
    inc cx
    jmp lapdoc  
    ketthuc:
    lea dx,NL
    mov ah,9
    int 21h 
    lea si,mang  
    laphienthi:     ;doan tu nay xuong la hien thi lai
    mov dl,[si]
    mov ah,2
    int 21h
    inc si
    loop laphienthi   
    
    mov ah,4ch
    int 21h
    main endp
 end main
