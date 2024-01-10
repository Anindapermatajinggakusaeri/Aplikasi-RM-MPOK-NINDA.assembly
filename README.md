include 'emu8086.inc'

cls macro
    mov ax,0600h
    mov cx,cx
    mov dx,184fh
    mov bh,7
    int 10h
    endm  

output macro string
    mov ah,09
    lea dx,string
    int 21h
    endm

input macro
    mov ah, 01h
    int 21h
    endm


.model small
.code
org 100h

Data:
    JMP Mulai
    
    menu    db 13,10,'+============================================================+',13,10
            db ':************>>>>>>>>>>>>MENU RM MPOK NINDA<<<<<<<<<<<<************:',13,10
            db '+==================================================================+',13,10
            db ':1.Paket Murah (Nasi Ayam Paha Bawah Bakar + Es teh)               :',13,10
            db ':  Rp. 12.000,-                                                    :',13,10
            db ':2.Paket Hemat (Nasi Ayam Sayap Bakar + Es teh)                    :',13,10
            db ':  Rp. 12.500,-                                                    :',13,10 
            db ':3.Paket Wareg (Nasi Ayam Sayap + Dada Bakar + Es teh)             :',13,10
            db ':  Rp. 20.000,-                                                    :',13,10
            db ':4.Paket Sewarege (Nasi Ayam goreng + Sayur Asem + Sambel + Es teh):',13,10
            db ':  Rp. 22.000,-                                                    :',13,10
            db ':5.Paket Kuah (Nasi Soto Ayam + Es teh)                            :',13,10
            db ':  Rp. 10.000,-                                                    :',13,10
            db ':6.Paket Ulek (Gado-gado + Es teh)                                 :',13,10
            db ':  Rp. 8.000,-                                                     :',13,10 
            db '+==================================================================+',13,10
            
     pil1   db 13,10,'  Membeli Paket Murah Rp. 12.000$' 
     pil2   db 13,10,'  Membeli Paket Hemat Rp. 12.500$'
     pil3   db 13,10,'  Membeli Paket Wareg Rp. 20.000$'
     pil4   db 13,10,'  Membeli Paket Sewarege Rp. 22.000$'
     pil5   db 13,10,'  Membeli Paket Kuah Rp. 10.000$'
     pil6   db 13,10,'  Membeli Paket Ulek Rp. 8.000$'  
     
     pert1  db 13,10,' Menu yang anda pilih:$'
     
Mulai:
    cls
    output menu
    putc 13
    putc 10
    
Mulai2:
    output pert1
 
Pilih:
    input
    putc 13
    putc 10
    cmp al, '1'
    je sa  
    cmp al, '2'
    je du
    cmp al, '3'
    je ti
    cmp al, '4'
    je em
    cmp al, '5'
    je li
    cmp al, '6'
    je en
    jne Mulai2
    
sa:
    mov ah,09h
    lea dx,pil1
    int 21h
    jmp selesai
    
du:
    mov ah,09h
    lea dx,pil2
    int 21h
    jmp selesai
    
ti: 
    mov ah,09h
    lea dx,pil3
    int 21h
    jmp selesai 
    
em:
    mov ah,09h
    lea dx,pil4
    int 21h
    jmp selesai
    
li:
    mov ah,09h
    lea dx,pil5
    int 21h
    jmp selesai    
        
en:
    mov ah,09h
    lea dx,pil6
    int 21h
    jmp selesai
    
selesai:
    end data
    end program                         
