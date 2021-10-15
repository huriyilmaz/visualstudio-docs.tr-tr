---
description: PerfView, Windows için Olay İzleme'ye dayalı ETL (olay izleme günlüğü) dosyaları oluşturan ve bu dosyalarla ilgili bazı sorunları gidermede yararlı Visual Studio.
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
ms.openlocfilehash: 45260d0e265f1c1104dad872528a7489994964da
ms.sourcegitcommit: 72f8ce4992cc62c4833e6dcb0f79febb328c44be
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2021
ms.locfileid: "130010658"
---
# <a name="collect-an-etl-trace-with-perfview-and-create-minidumps-with-all-call-stacks"></a>PerfView ile bir ETL izlemesi toplama ve tüm çağrı yığınları ile minidumps oluşturma

Microsoft ürün ekibi, Visual Studio sorun giderme için ek bilgi toplamak için bir ETL izlemesi veya minidump'lar talep edebilir. Bir ETL izlemesi toplamak veya tüm çağrı yığınları için minidumps oluşturmak için aşağıdaki adımları kullanın.

## <a name="collect-an-etl-trace-with-perfview"></a>PerfView ile ETL izlemesi toplama

PerfView, Windows için Olay İzleme'ye dayalı ETL (olay izleme günlüğü) dosyaları oluşturan ve bu dosyalarla ilgili bazı sorunları gidermede yararlı Visual Studio. [](/windows/desktop/ETW/event-tracing-portal) Bazen bir sorun bildirebilirsiniz; ürün ekibi sizden ek bilgi toplamak için PerfView'u çalıştırmayı sorabilir.

### <a name="install-perfview"></a>PerfView'u yükleme

perfView'u [GitHub.](https://github.com/Microsoft/perfview/blob/master/documentation/Downloading.md)

### <a name="run-perfview"></a>PerfView Çalıştırma

1. PerfView.exe **Gezgini'nde** Windows tıklayın ve Yönetici olarak **çalıştır'ı** seçin.
1. Topla menüsünde Topla'ya **tıklayın.**
1. **Zip,** **Merge** ve **ThreadTime denetimlerini kullanın.**
1. Döngüsel **MB'yi** 1000'e kadar artır.
1. EtL **izlemelerini** belirtilen bir klasöre ve birden çok kez topacaksanız Veri Dosyasına kaydetmek için Geçerli Dir'i kullanın.
1. Veri kaydetmeye başlamak için Koleksiyonu **Başlat düğmesini** seçin.
1. Veri kaydını durdurmak için Koleksiyonu Durdur **düğmesini** seçin. PrefView.etl.zip dosyası belirtilen dizine kaydedilir.

PerfView yalnızca arabelleğe sığan en son verileri depolar. Bu nedenle, yeniden donmaya veya yavaşlamaya başladıktan Visual Studio mümkün olan en kısa sürede koleksiyonu durdurmayı deneyin. Bir sorun olduktan sonra 30 saniyeden uzun bir süre toplamayın.

Daha fazla bilgi için bkz. [Channel9'da PerfView Öğreticisi.](https://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-1-Collecting-data-with-the-Run-command)

## <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>Tüm çağrı yığınları ile bir Visual Studio minidumps oluşturma

Bazı durumlarda Microsoft, tüm çağrı yığınları için bilgi Visual Studio çalışan bir işlem için bir minidump sorabilir. Bu bilgileri toplamak için şu adımları gerçekleştirin:

### <a name="create-the-minidump-file"></a>Minidump dosyasını oluşturma

1. Yeni bir örnek Visual Studio.
1. Ana menüden İşleme **Eklemede Hata**  >  **Ayıkla'ya tıklayın.**
1. İlgili Yönetilen ve **Yerel onay** **kutularını işaretleyin** ve Ekle'ye **basın.**

   ![İşleme Ekle iletişim kutusunda seçilen kod türlerini gösteren ekran görüntüsü.](../ide/media/attach-to-process.png)

1. Çalışan işlemler Visual Studio eklemek için diğer örnek örnek seçin.
1. Ana menüden Hata Ayıkla **Tüm Hata**  >  **Ayıklama'ya tıklayın.**
1. Ana menüden Döküm dökümlerini Farklı **Kaydet hata**  >  **ayıkla'ya tıklayın.**

### <a name="get-the-call-stacks-from-the-minidump"></a>Minidump'tan çağrı yığınlarını al

1. Döküm dosyasını Visual Studio.
1. Araçlar Seçenekler  >  **Sembollerde**  >  **Hata Ayıklama'ya** gidin ve Sembol dosyası  >   **(.pdb)**  konumlarında Microsoft Sembol Sunucularının işaretli olduğundan emin olun.
1. Komut penceresini **açın** (**Diğer Komut**  >  **Windows**  >  **Penceresini Görüntüle**).
1. '~*k' yazın. Pencerede tüm iş parçacıklarının çağrı yığınları görüntülenir.
1. Komut Penceresindeki tüm metni kopyalayın ve bir metin dosyasına kaydedin.
1. Txt dosyasını hataya iliştirin.
