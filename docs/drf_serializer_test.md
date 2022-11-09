from polls.models import Osoba <br />
from polls.serializers import OsobaSerializer <br />
from rest_framework.renderers import JSONRenderer <br />
from rest_framework.parsers import JSONParser <br />

osoba = Osoba(imie='Dominik', nazwisko='Kołakowski', miesiac_urodzenia=9) <br /> <br />
osoba.save() <br /><br />
serializer = OsobaSerializer(osoba) <br /><br />
serializer.data <br /><br />
output: {'id': 8, 'imie': 'Dominik', 'nazwisko': 'Kołakowski', 'miesiac_urodzenia': '9', 'kraj': None}<br />
content = JSONRenderer().render(serializer.data) <br /><br />
content <br /><br />
output: b'{"id":8,"imie":"Dominik","nazwisko":"Ko\xc5\x82akowski","miesiac_urodzenia":"9","kraj":null}'<br />
import io <br /><br />
stream = io.BytesIO(content) <br /><br />
data = JSONParser().parse(stream) <br /><br />
deserializer = OsobaSerializer(data=data) <br /><br />
deserializer.is_valid() <br /><br />
output: True <br /><br />
deserializer.errors <br />
Output: {} <br />
deserializer.fields <br />
Output: {'id': IntegerField(read_only=True), 'imie': CharField(required=True), 'nazwisko': CharField(required=True), 'miesiac_urodzenia': ChoiceField(choices=(('1', 'styczeń'), ('2', 'luty'), ('3', 'marzec'), ('4', 'kwiecień'), ('5', 'maj')
, ('6', 'czerwiec'), ('7', 'lipiec'), ('8', 'sierpień'), ('9', 'wrzesień'), ('10', 'październik'), ('11', 'listopad'), ('12', 'grudzień')), default='1'), 'kraj': PrimaryKeyRelatedField(allow_null=True, queryset=<QuerySet [<Druzyna: 
Polska (PL)>, <Druzyna: Mexico (MX)>, <Druzyna: Mexico (MX)>, <Druzyna: Germany (GE)>]>)}

deserializer.validated_data  <br /><br />
Output: OrderedDict([('imie', 'Dominik'), ('nazwisko', 'Kołakowski'), ('miesiac_urodzenia', '9'), ('kraj', None)]) <br />
deserializer.save()<br /><br />
OUTPUT: <Osoba: Dominik Kołakowski><br /><br />
deserializer.data<br /><br />
OUTPUT: {'id': 9, 'imie': 'Dominik', 'nazwisko': 'Kołakowski', 'miesiac_urodzenia': '9', 'kraj': None}<br /><br />



from polls.models import Druzyna<br /><br />
from polls.serializers import DruzynaSerializer<br /><br />
from rest_framework.renderers import JSONRenderer<br /><br />
from rest_framework.parsers import JSONParser<br /><br />
druzyna = Druzyna('PL', 'Janosiki();')    <br /><br />
druzyna.save()<br /><br />
serializer = DruzynaSerializer(druzyna)<br /><br />
serializer.data<br /><br />
OUTPUT: {'id': 3, 'kraj': 'PL', 'nazwa': 'Janosiki();'}<br /><br />
content = JSONRenderer().render(serializer.data)<br /><br />
content<br /><br />
OUTPUT: b'{'id': 3, 'kraj': 'PL', 'nazwa': 'Janosiki();'}'<br /><br />
import io<br /><br />
stream = io.BytesIO(content)<br /><br />
data = JSONParser().parse(stream)<br /><br />
deserializer = DruzynaSerializer(data=data) <br /><br />
deserializer.is_valid() <br /><br />
OUTPUT: True<br /><br />
deserializer.validated_data<br /><br />
OUTPUT: OrderedDict([('kraj', 'PL'), ('nazwa', 'Janosiki;')])<br /><br />
deserializer.save()<br /><br />
OUTPUT: <Druzyna: Janosiki(); (PL)><br /><br />
deserializer.data<br /><br />
OUTPUT: {'id': 4, 'kraj': 'PL', 'nazwa': 'Janosiki();'}<br /><br />