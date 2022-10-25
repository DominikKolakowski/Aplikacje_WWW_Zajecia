Zadanie 1:
(InteractiveConsole)
>>> from polls.models import Question, Osoba, Druzyna 
>>> Osoba.objects.all()    
<QuerySet [<Osoba: Jan Kowalski>, <Osoba: Robercik Lewandowski>, <Osoba: Juan Pablo>, <Osoba: Gorge Smith>]>

Zadanie 2:
>>> Osoba.objects.get(id=3) 
<Osoba: Gorge Smith>

Zadanie 3:
>>> Osoba.objects.filter(imie__startswith='R') 
<QuerySet [<Osoba: Robercik Lewandowski>]>

Zadanie 4:
Nie znalazłem tego

Zadanie 5:
>>> from polls.models import Druzyna
>>> Druzyna.objects.all().order_by('-nazwa')
<QuerySet [<Druzyna: Polska (PL)>, <Druzyna: Mexico (MX)>, <Druzyna: Germany (GE)>]>

Zadanie 6:
>>> from django.utils import timezone
>>> q = Osoba(imie='Paweł', nazwisko='Kulawy', miesiac_urodzenia=3, data_dodania=timezone.now()) 
>>> q.save()
