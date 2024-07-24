print('Hello,world!')

# Задача 1 по словарю:
from pprint import pprint
cook_book = {}
with open('recipes.txt','rt',encoding='utf-8') as book:
    dishes = " "
    for item in book:
        item = item.strip()
        if item.isdigit():
            continue
        elif item and '|' not in item:
            cook_book[item] = []
            dishes = item
        elif item and '|' in item:
            a,b,c = item.split("|")
            cook_book.get(dishes).append(dict(ingredient_name=a,quantity=int(b),measure=c))

pprint(cook_book)

# Задача 2 на вывод ингредиентов:
def get_shop_list_by_dishes(dishes, person_count):
    stop_list = dict()

    for dish_name in dishes:
        if dish_name in cook_book:
            for ingredient in cook_book[dish_name]:
                weight_list = dict()
                if ingredient['ingredient_name'] not in stop_list:
                    weight_list['measure'] = ingredient['measure']
                    weight_list['quantity'] = ingredient['quantity'] * person_count
                    stop_list[ingredient['ingredient_name']] = weight_list
                else:
                    stop_list[ingredient['ingredient_name']] ['quantity'] = stop_list[ingredient['ingredient_name']] ['quantity'] + ingredient['quantity'] * person_count

        else:
            print(f'Такое блюдо отсутствует!')
    return stop_list

# Задача 3 по слиянию файлов:



# !!!! Прошу выделить ещё немного времни на третью часть( Немного запутался в слиянии файлов.