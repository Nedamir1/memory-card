from PyQt5.QtCore import Qt
from PyQt5.QtWidgets import QApplication, QWidget, QHBoxLayout, QVBoxLayout, QGroupBox, QRadioButton,QPushButton, QLabel, QButtonGroup, QMessageBox
from random import shuffle, randint
app = QApplication([])
window = QWidget()
# Создаем панель вопроса
class Question():
    def __init__(self,question, right_answer, wrong1, wrong2, wrong3):
        self.question = question
        self.right_answer = right_answer
        self.wrong1 = wrong1
        self.wrong2 = wrong2
        self.wrong3 = wrong3


#Список вопросов и ответов!
question_list = []

question_list.append(Question('Государственный язык Бразилии' ,"Португальский", "Бразильский", "Испанский", "Итальянский"))
question_list.append(Question('Сколько мне лет?', 'много', "мало","много-мало","мало-много"))
question_list.append(Question('Сколько строк в коде?', "столько же, сколько мне лет", "100+","200+", "ладно"))
question_list.append(Question('Сколько будет 2+2?', "4", "не знаю", "танк Т-34", "немецкая противотанковая самоходная артиллерийская установка rheinmetall-borsig waffenträger"))
question_list.append(Question('Как зовут Дамира?', "Его не зовут, он сам приходит", "Дамир", "Андрей", "пон-пон"))
question_list.append(Question('Функция поджелудчной железы?', "переваривание питательных веществ", "Не нужная штука", "Переварение", "Защита организма"))
question_list.append(Question('Какого типа соединения костей не существует?', "Недвижимое", "подвижное", "полуподвижное", "..."))
question_list.append(Question("Каких веществ в костях детей больше?", "органических", "неорганических", "Бактрий", "обезьяны"))
question_list.append(Question("График функции y=kx2 проходит через точку (−2;28). Найдите k", "-7", "14", "-28", "-14"))
question_list.append(Question("Какая функция является прямой пропорциональностью?", "у = -1*х", "у = 0 * х", "у = х-1", "у = 1 - х"))
question_list.append(Question("Через какую точку проходит график функции у = 3х - 5?", "(1;-2)", "(2;-1)", "(-2;-1)", "(ne znau)"))
question_list.append(Question("Когда началась Вторая мировая война?", "1 сентября 1939", "1 октября 1939", "1941", "была только первая"))
question_list.append(Question("Кто руководил СССР в период Великой Отечественной войны?", "Иосиф Виссарионович Сталин", "Ленин", "Путин", "не было руководителя"))
question_list.append(Question("Что такое план «Барбаросса»?", "План нападения фашисткой Германии на СССР", "нет такого слова", "я не знаю", "да"))
question_list.append(Question("Как создать словарь?", "dict()", "list()", "def create_dict()", "break"))
question_list.append(Question("Вам понравился тест?", "да", "нет", "да нет", "нет да"))
question_list.append(Question("Это конец?", "нет", "да", "да", "да"))
question_list.append(Question("Долго я думал вопросы?", "половина с интернета", "нет", "да", "не думал"))
question_list.append(Question("Теперь это конец?", "нет", "нет", "нет", "нет"))
question_list.append(Question('Сколько клавиш на стандартной клавиатуре?', "104", "1","45","100"))
question_list.append(Question('Сколько костей у взрослого человека?',"206-208", "200","150","300"))
question_list.append(Question('Что из этого относится к строению сердца?',"Правый желудочек","левая нога","правая нога","кровь"))
question_list.append(Question('Сколько пальцев у пингвина если у жирафа на лбу рога вместо ноги)',"3 пальцерогоноги","4 пальца", "я душнила, поэтому у жирафа нет пальцев", "не знаю"))
question_list.append(Question('Почему утконос, а не уткоклюв?', "Создатель сам не знает ответа", "потому что потому", " ладно","ладнох2"))
question_list.append(Question('Можно ли назвать сломанный экскалатор лестницей?', "ДА!", "НЕТ!", "пон пон", "я не знаю"))
question_list.append(Question('Что делать, если мой унитаз танцует?', "Танцевать с ним", "Купить противоунитазно-танцевальное средство", "я не знаю", "я душнила поэтому глупый вопрос"))
question_list.append(Question('А как я буду звать Красную Шапочку, если она снимет красную шапочку?', "Алена", "маша", "вика", "дамир"))
question_list.append(Question('Почему дед другую бабку у рыбки не попросил?', "Тупанул", "сильно любил бабку", "не знаю", "ладно"))
question_list.append(Question('Почему пушкин был темнокожим?', "У него дедушка африканец", "не знаю", "Дамир разрешил", "Он приёмный"))
question_list.append(Question('Кто убил Пушкина?', "Дантес", "Гоголь", "Не знаю", "ладно"))

btn_OK = QPushButton('Ответить')
lb_Question = QLabel('Самый сложный вопрос в мире!')

RadioGroupBox = QGroupBox("Варианты ответов")
 
rbtn_1 = QRadioButton('Вариант 1')
rbtn_2 = QRadioButton('Вариант 2')
rbtn_3 = QRadioButton('Вариант 3')
rbtn_4 = QRadioButton('Вариант 4')
RadioGroup = QButtonGroup()
RadioGroup.addButton(rbtn_1)
RadioGroup.addButton(rbtn_2)
RadioGroup.addButton(rbtn_3)
RadioGroup.addButton(rbtn_4)
layout_ans1 = QHBoxLayout()   
layout_ans2 = QVBoxLayout()
layout_ans3 = QVBoxLayout()
layout_ans2.addWidget(rbtn_1) # два ответа в первый столбец
layout_ans2.addWidget(rbtn_2)
layout_ans3.addWidget(rbtn_3) # два ответа во второй столбец
layout_ans3.addWidget(rbtn_4)

layout_ans1.addLayout(layout_ans2)
layout_ans1.addLayout(layout_ans3)
 
RadioGroupBox.setLayout(layout_ans1)

# Создаем панель результата
AnsGroupBox = QGroupBox("Результат теста")
lb_Result = QLabel('прав ты или нет?') # здесь размещается надпись "правильно" или "неправильно"
lb_Correct = QLabel('ответ будет тут!') # здесь будет написан текст правильного ответа

layout_res = QVBoxLayout()
layout_res.addWidget(lb_Result, alignment=(Qt.AlignLeft | Qt.AlignTop))
layout_res.addWidget(lb_Correct, alignment=Qt.AlignHCenter, stretch=2)
AnsGroupBox.setLayout(layout_res)
 
# Размещаем все виджеты в окне:
layout_line1 = QHBoxLayout() # вопрос
layout_line2 = QHBoxLayout() # варианты ответов или результат теста
layout_line3 = QHBoxLayout() # кнопка "Ответить"
 
layout_line1.addWidget(lb_Question, alignment=(Qt.AlignHCenter | Qt.AlignVCenter))
# Размещаем в одной строке обе панели, одна из них будет скрываться, другая показываться:
layout_line2.addWidget(RadioGroupBox)   
layout_line2.addWidget(AnsGroupBox)  
RadioGroupBox.hide() # эту панель мы уже видели, скроем, посмотрим, как получилась панель с ответом
 
layout_line3.addStretch(1)
layout_line3.addWidget(btn_OK, stretch=2) # кнопка должна быть большой
layout_line3.addStretch(1)

# Теперь созданные строки разместим друг под другой:
layout_card = QVBoxLayout()
layout_card.addLayout(layout_line1, stretch = 3)
layout_card.setSpacing(5) # пробелы между содержимымh(1)ayout(layout_line1, stretch=2)
layout_card.addLayout(layout_line2, stretch=8)
layout_card.addStretch(1)
layout_card.addLayout(layout_line3, stretch=1)
layout_card.addStretch(1)
layout_card.setSpacing(5)


layout_card.addStretch(1)
window.setWindowTitle('Memory Card')

window.setLayout(layout_card)
window.resize(400,200)
def show_result(): #кнопка "следующий вопрос"
    RadioGroupBox.hide()
    AnsGroupBox.show()
    btn_OK.setText("следующий вопрос")
def show_question(): 
    RadioGroupBox.show()
    AnsGroupBox.hide()
    btn_OK.setText("Ответить!")
    RadioGroup.setExclusive(False)
    rbtn_1.setChecked(False)
    rbtn_2.setChecked(False)
    rbtn_3.setChecked(False)
    rbtn_4.setChecked(False)
    RadioGroup.setExclusive(True)
answers = [rbtn_1,rbtn_2,rbtn_3,rbtn_4]
def ask(q: Question):
    shuffle(answers)
    answers[0].setText(q.right_answer)
    answers[1].setText(q.wrong1)
    answers[2].setText(q.wrong2)
    answers[3].setText(q.wrong3)
    lb_Question.setText(q.question)
    lb_Correct.setText(q.right_answer)
    show_question()

def show_correct(res):
    lb_Result.setText(res)
    show_result()
def check_answer():
    if answers[0].isChecked():
        show_correct('Правильно!')
        window.score += 1
    else:
        if answers[1].isChecked() or answers[2].isChecked() or answers[3].isChecked():
            show_correct('Неправильно!')
            window.score -= 1
def next_question():
    len_ = len(question_list)
    point = ((window.score/len_)) * 100
    window.total += 1
    print('Всего вопросов:', window.total)
    print('Правильных ответов:', window.score)
    print('Stats', point, '%')
    cur_question = randint(0, len(question_list) - 1)
    if cur_question >= len(question_list):
        cur_question = 0
    q = question_list[cur_question]
    ask(q)
def click_OK():
    if btn_OK.text() == 'Ответить!':
        check_answer()
    else:
        next_question()

q = input('Хотите добавить свой вопрос?').lower()
if q == 'да':
    window.hide()
    question1 = input('Какой вопрос?')
    right_answer1 = input('Правильный ответ')
    
    wrong_answer1 = input('1 неправильный ответ:')
    wrong_answer2 = input('2 неправильный ответ:')
    wrong_answer3 = input('3 неправильный ответ:')
    
    question_list.append(Question(question1, right_answer1, wrong_answer1, wrong_answer2, wrong_answer3))


window.setLayout(layout_card)
btn_OK.clicked.connect(click_OK)
window.total = 0
window.score = 0
cur_question = -1
next_question()
window.show()
app.exec_()
