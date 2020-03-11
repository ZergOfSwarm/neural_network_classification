## Neural network classification

### Честно стырено здесь.
Описание на [youtube](https://www.youtube.com/watch?v=KL-zI-2Ifrs)

### Installation
#### 1. Скачиваем архив цветов от сюда ["flower_photos.tgz"](http://download.tensorflow.org/example_images/flower_photos.tgz)
и распаковываем к примеру в /home/user/flower_photos/
#### 2. Устанавливаем tensorflow v1.15 
pip install tensorflow==1.15 
При установки удалит другие версии tensorflow-2.1.0 если установлены!
#### 3. Скрипт "retrain.py" дообучения моделей можно взять отсюда:
["retrain.py"](https://raw.githubusercontent.com/tensorflow/hub/r0.1/examples/image_retraining/retrain.py)
#### 4. Запускаем скрипт для обучения нашей сети указав путь до наших цветочков.
python retrain.py --image_dir /home/user/flower_photos
#### 5. Создаем скрипт "label_image.py" код берем от сюда. Это скрипт будет распозновать неопознаные цветочки
["label_image.py"](https://raw.githubusercontent.com/tensorflow/tensorflow/master/tensorflow/examples/label_image/label_image.py)
#### 6. Запускаем разпознаение неопознаного цветочка при помощи команды указав путь до /home/user/flower_photos/recognition/12345.jpg
python label_image.py \
 --graph=/tmp/output_graph.pb \
  --labels=/tmp/output_labels.txt \
  --input_layer=Placeholder \
  --output_layer=final_result \
  --image /home/user/flower_photos/recognition/12345.jpg

или так
тюльпан
python label_image.py \--graph=/tmp/output_graph.pb \--labels=/tmp/output_labels.txt \--input_layer=Placeholder \--output_layer=final_result \--image /home/denis/flower_photos/recognition/12345.jpg

PS - папку "recognition" сохранить к примеру здесь /home/denis/flower_photos/recognition в том месте где распакован архив "flower_photos.tgz".

В итоге
tulips 0.9987852
roses 0.0009722363
sunflowers 0.00014587125
daisy 9.372772e-05
dandelion 2.960437e-06

роза
python label_image.py \--graph=/tmp/output_graph.pb \--labels=/tmp/output_labels.txt \--input_layer=Placeholder \--output_layer=final_result \--image /home/denis/flower_photos/recognition/54321.jp

В итоге
roses 0.8905987
tulips 0.05101582
sunflowers 0.028663497
daisy 0.023395414
dandelion 0.006326692

маргаритка/daisy
python label_image.py \--graph=/tmp/output_graph.pb \--labels=/tmp/output_labels.txt \--input_layer=Placeholder \--output_layer=final_result \--image /home/denis/flower_photos/recognition/4.jpg

В итоге
daisy 0.9956761
sunflowers 0.0023719026
dandelion 0.0012801972
roses 0.000459438
tulips 0.00021229866

одуванчик/dandelion
python label_image.py \--graph=/tmp/output_graph.pb \--labels=/tmp/output_labels.txt \--input_layer=Placeholder \--output_layer=final_result \--image /home/denis/flower_photos/recognition/2.jpg

В итоге
dandelion 0.9823454 / dandelion 0.9990777 (для 2a.jpg)
sunflowers 0.01608138
daisy 0.0014325682
tulips 7.8642726e-05
roses 6.200551e-05


python label_image.py \--graph=/tmp/output_graph.pb \--labels=/tmp/output_labels.txt \--input_layer=Placeholder \--output_layer=final_result \--image /home/denis/flower_photos/recognition/1.jpeg

sunflowers 0.67337984 / sunflowers 0.9918658 (для 1a.jpeg)
daisy 0.26449472
dandelion 0.053949982
roses 0.0053645317
tulips 0.002810898
