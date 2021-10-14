---
description: perfview, Visual Studio bazı tür sorunları gidermede yararlı olabilecek, Windows için olay izlemeyi temel alan ETL (olay izleme günlüğü) dosyaları oluşturan bir araçtır.
title: PerfView ile bir ETL izlemesi toplayın ve tüm çağrı yığınları ile mini dökümler oluşturun
ms.date: 10/11/2021
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
ms.openlocfilehash: 575ca63a4064de5f7d342495b9ad21a5a9d2a7e8
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129973307"
---
# <a name="collect-an-etl-trace-with-perfview-and-create-minidumps-with-all-call-stacks"></a>PerfView ile bir ETL izlemesi toplayın ve tüm çağrı yığınları ile mini dökümler oluşturun

Visual Studio bir sorun rapor ettiğinizde, Microsoft ürün ekibi, sorun giderme konusunda ek bilgi toplamak için bir ETL izlemesi veya mini döküm isteyebilir. Bir ETL izlemesini toplamak veya tüm çağrı yığınları için mini döküm oluşturmak için aşağıdaki adımları kullanın.

## <a name="collect-an-etl-trace-with-perfview"></a>PerfView ile ETL izlemesi toplama

perfview, Visual Studio bazı sorun sorunlarını gidermede faydalı olabilecek [Windows için olay izleme](/windows/desktop/ETW/event-tracing-portal) tabanlı ETL (olay izleme günlüğü) dosyaları oluşturan bir araçtır. Bazen bir sorun rapor ettiğinizde, ürün ekibi ek bilgi toplamak için PerfView çalıştırmanızı isteyebilir.

### <a name="install-perfview"></a>PerfView 'ı yükler

[GitHub](https://github.com/Microsoft/perfview/blob/master/documentation/Downloading.md)PerfView öğesini indirin.

### <a name="run-perfview"></a>PerfView çalıştırma

1. Windows gezgini 'nde **PerfView.exe** sağ tıklayıp **yönetici olarak çalıştır** ' ı seçin.
1. Topla menüsünde **topla**' yı seçin.
1. **Zip**, **birleştirme** ve **threadtime**'ı denetleyin.
1. **DAIRESEL MB** ile 1000 arasında bir artış yapın.
1. Birden çok kez toplanmanız durumunda ETL izlemelerini belirtilen bir klasöre ve veri dosyasına kaydetmek için **geçerli dizini** değiştirin.
1. Veri kaydetmeye başlamak için **koleksiyonu Başlat** düğmesini seçin.
1. Verileri kaydetmeyi durdurmak için **koleksiyonu durdur** düğmesini seçin. PrefView.etl.zip dosya belirtilen dizine kaydedilir.

PerfView yalnızca kendi arabelleğine sığan en son verileri saklayabilir. bu nedenle, Visual Studio dondurma veya yavaşlamaya başladıktan sonra toplamayı en kısa sürede durdurmayı deneyin. Bir sorunla karşılaşmadan 30 saniyeden uzun süre toplanmayın.

Daha fazla bilgi için bkz. [Channel9 üzerinde PerfView öğreticisi](https://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-1-Collecting-data-with-the-Run-command).

## <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>tüm çağrı yığınlarıyla bir Visual Studio işlemi için mini dökümler oluşturma

bazı durumlarda Microsoft, çalışan bir Visual Studio işleminin tüm çağrı yığınlarıyla ilgili bilgilerle ilgili bir mini döküm isteyebilir. Bu bilgileri toplamak için şu adımları uygulayın:

### <a name="create-the-minidump-file"></a>Mini döküm dosyası oluşturma

1. Visual Studio yeni bir örneğini başlatın.
1. Ana menüden,   >  **işleme Ekle** Hata Ayıkla ' yı seçin.
1. İlgili **yönetilen** ve **Yerel** onay kutularını işaretleyin ve **Ekle**'ye basın.

   ![İşleme ekle](../ide/media/attach-to-process.png)

1. çalışan işlemlerin listesinden iliştirilecek diğer Visual Studio örneğini seçin.
1. Ana menüden **Hata Ayıkla**  >  **Tümünü kes**' i seçin.
1. Ana menüden,   >  **dökümü farklı kaydet kayıt** Ayıkla ' yı seçin.

### <a name="get-the-call-stacks-from-the-minidump"></a>Mini döküm dosyasından çağrı yığınlarını al

1. Döküm dosyasını Visual Studio ' de açın.
1. **Araçlar**  >  **Seçenekler**  >  **hata ayıklama**  >  **simgeleri** ' ne gidin ve **sembol dosyası (. pdb) konumlarında** **Microsoft sembol sunucularının** işaretli olduğundan emin olun.
1. **komut** penceresini açın (  >  **diğer Windows**  >  **komut penceresini** görüntüleyin).
1. ' ~ * K ' yazın. Pencerede tüm iş parçacıklarının çağrı yığınları görüntülenir.
1. Komut penceresinden tüm metni kopyalayın ve bir metin dosyasına kaydedin.
1. Txt dosyasını hataya iliştirin.
