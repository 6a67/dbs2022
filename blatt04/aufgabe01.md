# Aufgabe 1

## 1
a)  A ist ein Schlüsselkandidat
b)  AB ist ein Superschlüssel
c)  C ist weder Schlüsselkandidat noch Superschlüssel
d)  E ist weder Schlüsselkandidat noch Superschlüssel
e)  BDE ist Superschlüssel

## 2
Linksreduktion: \
Teste für AB 

Hülle(F, A):
    A Teilmenge von A -> AB
    AB Teilmenge von AB -> ABCDE

Daraus folgt, dass AB -> CDE zu A -> CDE reduziert werden kann

Hülle(F, B):
    A keine Teilmenge von B
    AB keine Teilmenge von B
    C keine Teilmenge von B
    E keine Teilmenge von B
    BDE keine Teilmenge von B



Teste für BDE

Hülle(F, B):
    Siehe ersten Teil

Hülle(F, D):
    A keine Teilmenge von D
    AB keine Teilmenge von D
    C keine Teilmenge von D
    E keine Teilmenge von D
    BDE keine Teilmenge von D

Hülle(F, E):
    A keine Teilmenge von E
    AB keine Teilmenge von E
    C keine Teilmenge von E
    E Teilmenge von E -> ED
    BDE keine Teilmenge von D

Keine sind überflüssig


**Zwischenergebnis**
1) A -> B
2) A -> CDE
3) C -> DE
4) E -> D
5) BDE -> AC


Rechtsreduktion: \
    $B \in AttrHülle(F - (A \rightarrow B) \cup (A \rightarrow (A-B)), A)$ \
    $H^{\prime}=AttrHülle(\{A \rightarrow CDE,\ C \rightarrow DE,\ E \rightarrow D,\ BDE \rightarrow AC\}, A)$ \
    Hülle(F', A): \
        A Teilmenge von A -> ACDE
        C Teilmenge von ACDE -> ACDE
        E Teilmenge von ACDE -> ACDE
        BDE keine Teilmenge von ACDE
    => B ist kein Element der neuen Attributhülle, somit muss B bleiben

## TODO: Muss man das nicht überprüfen, wenn rechts nur ein Element steht?

Reduktion für FD 2:
Teste C in AttrHülle(F - FD(2) + (A -> DE), A):
    AttrHülle(F', A):
        A Teilmenge von A -> AB
        A Teilmenge von AB -> ABDE
        C keine Teilmenge von ABDE
        E Teilmenge von ABDE -> ABDE
        BDE Teilmenge von ABDE -> ABCDE
    
    Somit ist C Element der AttrHülle(F', A) und somit überflüssig


Teste D in AttrHülle(F - FD(2) + (A -> E), A):
    AttrHülle(F', A):
        A Teilmenge von A -> AB
        A Teilmenge von AB -> ABE
        C keine Teilmenge von ABE
        E Teilmenge von ABE -> ABDE
        BDE Teilmenge von ABDE -> ABCDE

    Somit ist D Element der AttrHülle(F', A) und somit überflüssig

Teste E in AttrHülle(F - FD(2) + (A -> empty), A):
    AttrHülle(F', A):
        A Teilmenge von A -> AB
        A Teilmenge von AB -> AB
        C keine Teilmenge von AB
        E keine Teilmenge von AB
        BDE keine Teilmenge von AB

    Somit ist E kein Element der AttrHülle(F', A) und somit benötigt

=> FD(2): A -> E


Reduktion für FD(3):

Teste D in AttrHülle(F - FD(3) + (C -> E), C):
    AttrHülle(F', C):
        A keine Teilmenge von C
        A keine Teilmenge von C
        C Teilmenge von C -> CE
        E Teilmenge von CE -> CDE
        BDE keine Teilmenge von CDE

    Somit ist D Element der AttrHülle(F', C) und somit überflüssig

Teste E in AttrHülle(F - FD(3) + (C -> empty), C):
    AttrHülle(F', C):
        A keine Teilmenge von C
        A keine Teilmenge von C
        C Teilmenge von C -> C
        E keine Teilmenge von C
        BDE keine Teilmenge von C

    Somit ist E kein Element der AttrHülle(F', A) und somit benötigt

=> FD(3): C -> E


Reduktion für FD(4):

Teste D in AttrHülle(F - FD(4) + (E -> empty), E):
    AttrHülle(F', E):
        A keine Teilmenge von E
        A keine Teilmenge von E
        C keine Teilmenge von E
        E Teilmenge von E -> E
        BDE keine Teilmenge von E
    
    Somit ist D kein Element der AttrHülle(F', E) und somit benötigt

=> FD(4): C -> E


Reduktion für FD(5):

Teste BDE in AttrHülle(F - FD(3) + (C -> E), C):
    AttrHülle(F', C):
        A keine Teilmenge von C
        A keine Teilmenge von C
        C Teilmenge von C -> CE
        E Teilmenge von CE -> CDE
        BDE keine Teilmenge von CDE