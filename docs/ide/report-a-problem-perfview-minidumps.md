---
description: PerfView, Windows için Olay İzleme'ye dayalı ETL (olay izleme günlüğü) dosyaları oluşturan ve Visual Studio ile ilgili bazı sorunları gidermede yararlı Visual Studio.
title: PerfView ile bir ETL izlemesi toplama ve tüm çağrı yığınları ile minidumps oluşturma
ms.date: 10/12/2021
ms.topic: how-to
helpviewer_keywords:
- perfview
- ETL Trace
- minidumps for Visual Studio issues"
author: corob-msft
ms.author: corob
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Collect ETL traces using perfview.exe and create minidumps to send to Microsoft, for troubleshooting issues with Visual Studio
ms.openlocfilehash: 2a5d6e01fa737ce44bff4307eacebc1b7dedc22f
ms.sourcegitcommit: fc874be3fe4637a23997b4ef2d99a2ee9a499581
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "135517742"
---
# <a name="collect-an-etl-trace-with-perfview-and-create-minidumps-with-all-call-stacks"></a>PerfView ile bir ETL izlemesi toplama ve tüm çağrı yığınları ile minidumps oluşturma

Microsoft ürün ekibi, Visual Studio sorun giderme için ek bilgi toplamak için bir ETL izlemesi veya minidump'lar talep edebilir. Bir ETL izlemesi toplamak veya tüm çağrı yığınları için minidumps oluşturmak için aşağıdaki adımları kullanın.

## <a name="collect-an-etl-trace-with-perfview"></a>PerfView ile ETL izlemesi toplama

PerfView, Windows için Olay İzleme'ye dayalı ETL (olay izleme günlüğü) dosyaları oluşturan ve Visual Studio ile ilgili bazı sorunları gidermede yararlı Visual Studio. [](/windows/desktop/ETW/event-tracing-portal) Bazen bir sorun bildirebilirsiniz; ürün ekibi sizden ek bilgi toplaması için PerfView'u çalıştırmayı sorabilir.

### <a name="install-perfview"></a>PerfView'u yükleme

perfView'u [GitHub.](https://github.com/Microsoft/perfview/blob/master/documentation/Downloading.md)

### <a name="run-perfview"></a>PerfView Çalıştırma

1. Windows **Gezgini'nde** PerfView.exesağ tıklayın ve Yönetici olarak **çalıştır'ı** seçin.
1. Topla menüsünde Topla'ya **tıklayın.**
1. **Zip,** **Merge** ve **ThreadTime denetimlerini kullanın.**
1. Döngüsel **MB'yi** 1000'e kadar artır.
1. EtL **izlemelerini** birden çok kez topacaksanız belirtilen klasöre ve Veri Dosyasına kaydetmek için Geçerli Dir'i kullanın.
1. Veri kaydetmeye başlamak için Koleksiyonu **Başlat düğmesini** seçin.
1. Veri kaydını durdurmak için Koleksiyonu Durdur **düğmesini** seçin. PrefView.etl.zip dosyası belirtilen dizine kaydedilir.

PerfView yalnızca arabelleğine sığan en son verileri depolar. Bu nedenle, yeniden donmaya veya yavaşlamaya başladıktan Visual Studio mümkün olan en kısa sürede koleksiyonu durdurmayı deneyin. Bir sorun olduktan sonra 30 saniyeden uzun bir süre toplamayın.

## <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>Tüm çağrı yığınları ile bir Visual Studio için minidumps oluşturma

Bazı durumlarda Microsoft, tüm çağrı yığınları için bilgi Visual Studio çalışan bir işlem için bir minidump sorabilir. Bu bilgileri toplamak için şu adımları gerçekleştirin:

### <a name="create-the-minidump-file"></a>Minidump dosyasını oluşturma

1. Yeni bir örnek Visual Studio.
1. Ana menüden İşleme **Eklemede Hata**  >  **Ayıkla'ya tıklayın.**
1. İlgili Yönetilen ve **Yerel onay** **kutularını işaretleyin** ve Ekle'ye **basın.**

   ![İşleme Ekle iletişim kutusunda seçilen kod türlerini gösteren ekran görüntüsü.](../ide/media/attach-to-process.png)

1. Çalışan işlemler Visual Studio eklemek istediğiniz diğer örnek örneği seçin.
1. Ana menüden Hata Ayıkla **Tüm Hataları**  >  **Ayıkla'ya tıklayın.**
1. Ana menüden Döküm dökümlerini Farklı **Kaydet hata**  >  **ayıkla'ya tıklayın.**

### <a name="get-the-call-stacks-from-the-minidump"></a>Minidump'tan çağrı yığınlarını al

1. Döküm dosyasını Visual Studio.
1. Araçlar Seçenekler **Hata** Ayıklama Sembolleri'ne gidin ve Sembol dosyası  >    >    >   **(.pdb)**  konumlarında Microsoft Sembol Sunucularının işaretli olduğundan emin olun.
1. Komut penceresini **açın** (**Diğer Komut**  >  **Windows**  >  **Penceresini Görüntüle**).
1. '~*k' yazın. Pencerede tüm iş parçacıklarının çağrı yığınları görüntülenir.
1. Komut Penceresindeki tüm metni kopyalayın ve bir metin dosyasına kaydedin.
1. Txt dosyasını hataya iliştirin.
