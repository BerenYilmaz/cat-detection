# YOLO ile Kedi Tespiti

Tek s�n�fl� bir kedi veri k�mesi �zerinde YOLO e�itimi ve �rnek g�r�nt�de tahmin �al��mas�. `train.ipynb`, e�itim ve ��kar�m h�crelerini birlikte i�erir.

## Kurulum

Depo k�k�nde etkin bir Python sanal ortam�nda:

```powershell
python -m pip install -r requirements.txt
jupyter notebook train.ipynb
```

## Veri ve e�itim

[Cat Project v4](https://universe.roboflow.com/berens-workspace-ont4h/cat-project-7eutw/dataset/4) veri k�mesini YOLO bi�iminde indirip `Cat_Project.v4i.yolov11/` i�ine a��n. Kaynak yap�land�rmas� CC BY 4.0 lisans� ve tek `Cat` s�n�f�n� belirtir. G�rseller ve etiketler depoya dahil de�ildir; `data.yaml` ve kaynak bildirimleri korunur.

E�itim h�cresi `yolo11n.pt` ba�lang�� a��rl�klar�n� kullan�r ve `epochs=32`, `imgsz=640` ile �al���r. Ba�lang�� a��rl�klar�n� sa�lay�n veya Ultralytics'in indirme mekanizmas� i�in internet eri�imi kullan�n. `data.yaml` i�indeki e�itim/do�rulama yollar�n� kontrol edin.

## Tahmin

E�itimden sonra ikinci h�credeki `runs/detect/train-13/weights/best.pt` yolunu kendi e�itim ��kt�n�zdaki `best.pt` yoluyla de�i�tirin. Bu yol sabittir ve yeni e�itimle otomatik g�ncellenmez.

Tahmin `cats.jpeg` �zerinde `conf=0.5`, `iou=0.4`, `agnostic_nms=True`, `max_det=100` ayarlar�yla yap�l�r. Sonu� ekranda a��l�r ve `result.jpg` olarak kaydedilir; mevcut dosyan�n �zerine yaz�l�r. `cats.jpeg`, `images.jpg` ve �nceki bir �rnek sonu� g�rseli depoda bulunur.

Notebook ��kt�lar� temizlenmi�tir; e�itilmi� a��rl�klar ve e�itim g�nl�kleri dahil de�ildir. Kaydedilmi� sonu� g�rseli do�rulanm�� bir ba�ar� metri�i de�ildir. H�crelerdeki `KMP_DUPLICATE_LIB_OK` ayar� eski yerel ortam ge�ici ��z�m�d�r; ba��ml�l�k uyumlulu�unu garanti etmez.
