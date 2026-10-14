# YOLO ile Kedi Tespiti

Tek sınıflı bir kedi veri kümesi üzerinde YOLO eğitimi ve örnek görüntüde tahmin çalışması. `train.ipynb`, eğitim ve çıkarım hücrelerini birlikte içerir.

## Kurulum

Depo kökünde etkin bir Python sanal ortamında:

```powershell
python -m pip install -r requirements.txt
jupyter notebook train.ipynb
```

## Veri ve eğitim

[Cat Project v4](https://universe.roboflow.com/berens-workspace-ont4h/cat-project-7eutw/dataset/4) veri kümesini YOLO biçiminde indirip `Cat_Project.v4i.yolov11/` içine açın. Kaynak yapılandırması CC BY 4.0 lisansı ve tek `Cat` sınıfını belirtir. Görseller ve etiketler depoya dahil değildir; `data.yaml` ve kaynak bildirimleri korunur.

Eğitim hücresi `yolo11n.pt` başlangıç ağırlıklarını kullanır ve `epochs=32`, `imgsz=640` ile çalışır. Başlangıç ağırlıklarını sağlayın veya Ultralytics'in indirme mekanizması için internet erişimi kullanın. `data.yaml` içindeki eğitim/doğrulama yollarını kontrol edin.

## Tahmin

Eğitimden sonra ikinci hücredeki `runs/detect/train-13/weights/best.pt` yolunu kendi eğitim çıktınızdaki `best.pt` yoluyla değiştirin. Bu yol sabittir ve yeni eğitimle otomatik güncellenmez.

Tahmin `cats.jpeg` üzerinde `conf=0.5`, `iou=0.4`, `agnostic_nms=True`, `max_det=100` ayarlarıyla yapılır. Sonuç ekranda açılır ve `result.jpg` olarak kaydedilir; mevcut dosyanın üzerine yazılır. `cats.jpeg`, `images.jpg` ve önceki bir örnek sonuç görseli depoda bulunur.

Notebook çıktıları temizlenmiştir; eğitilmiş ağırlıklar ve eğitim günlükleri dahil değildir. Kaydedilmiş sonuç görseli doğrulanmış bir başarı metriği değildir. Hücrelerdeki `KMP_DUPLICATE_LIB_OK` ayarı eski yerel ortam geçici çözümüdür; bağımlılık uyumluluğunu garanti etmez.
