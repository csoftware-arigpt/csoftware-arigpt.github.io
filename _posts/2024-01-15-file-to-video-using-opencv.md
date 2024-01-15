---
layout: post
title: Конвертация из файла в видео используя OpenCV
---

Всем привет, csoftware на свзяи

В этом посте будем разбиратся, как конвертировать файл в видео

У многих сразу появится вопрос - зачем а главное нафига?
Сразу отвечу на вас вопрос: Через конвертацию мы сможем использовать YouTube в качестве файлообменнмика

Возьмём кусок кода из [этого проекта](https://github.com/lewangdev/youtube-drive) и проанализируем его

```python
fd = open(infile_path, 'rb')
raw_data_bytes = fd.read()
data_bytes = np.frombuffer(raw_data_bytes, dtype=np.uint8)
len_of_data = len(data_bytes)
num_bytes_per_row = int(num_cols_per_frame * 3 / 8)
num_bytes_per_frame = num_bytes_per_row * num_rows_per_frame

len_bytes = np.array(bytearray(len_of_data.to_bytes(4, byteorder='big')), dtype=np.uint8)
(num_frames, num_leftover_bytes) = quotient_remainder(4 + len_of_data, num_bytes_per_frame)

if num_leftover_bytes > 0:
        num_bytes_last_frame_padding = num_bytes_per_frame - num_leftover_bytes
        padding_bytes = np.full((num_bytes_last_frame_padding), 0, dtype=np.uint8)
        data_bytes = np.concatenate((len_bytes, data_bytes, padding_bytes))
        num_frames += 1
else:
        data_bytes = np.concatenate((len_bytes, data_bytes))

size = (num_cols_per_frame * 20, num_rows_per_frame * 20)

video = cv2.VideoWriter(outvideo_path, cv2.VideoWriter_fourcc(
        *'mp4v'), fps, size)

for i in range(num_frames):
        frame_bytes = data_bytes[i * num_bytes_per_frame: (i + 1) * num_bytes_per_frame]
        frame_bits = np.unpackbits(frame_bytes)
        # Reshape array to array(36， 72， 3)
        frame = color_value(frame_bits).reshape(num_rows_per_frame, num_cols_per_frame, 3)
        img = Image.fromarray(frame, mode="RGB")
        # Scale image to (1280, 720)
        newimg = img.resize(size, Image.Resampling.BOX)
        video.write(np.asarray(newimg))
fd.close()
```

Первым делом мы читаем файл в бинарном виде и сохраняем в переменной raw_data_bytes
Дальше идет конвертация в буффер uint8 средствами NumPY
Дальше по параметрам идет просчет байтов в ряд и в кадр

Пост недопилен, приду домой и допишу
