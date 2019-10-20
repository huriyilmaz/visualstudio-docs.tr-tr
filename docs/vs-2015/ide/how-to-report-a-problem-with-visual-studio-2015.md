---
title: Visual Studio 2015 ile ilgili sorun bildirme | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
ms.assetid: 24ecb76e-b7ad-432d-88ab-d9849963465d
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e75215d2693b5fe2bf879c4b293ae853b42905e7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651779"
---
# <a name="how-to-report-a-problem-with-visual-studio-2015"></a>Visual Studio 2015 ile İlgili Sorun Bildirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ile ilgili en son belgeler için bkz. [Visual Studio 'da sorun bildirme](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

Visual Studio 2015 ile ilgili bir sorunla karşılaşırsanız, bunu tanılayıp çözebilmemiz için hakkında bilgi sahibi olmak istiyoruz.  **Sorun bildir** aracını kullanarak, sorun hakkında ayrıntılı bilgi toplayabilir ve yalnızca birkaç düğme tıklamasıyla Microsoft 'a gönderebilirsiniz.

Microsoft gizliliğinize saygı duyar. Bize göndereceğiniz verileri nasıl değerlendiyoruz hakkında daha fazla bilgi için, [Microsoft Visual Studio ürün ailesi gizlilik bildirimi](https://www.visualstudio.com/dn948229)' ne bakın.

## <a name="open-the-report-a-problem-tool"></a>Sorun bildir aracını açın

Başlık çubuğunda **Hızlı Başlat** ' ın yanındaki Kullanıcı geri bildirimi simgesine tıklayın veya **sorun bildirmek > yardım > geri bildirim gönder**' e tıklayın.

![Sorun bir menü öğesi bildirin](../ide/media/report-a-problem-menu-item.png "Sorun bir menü öğesi bildirin")

## <a name="describe-the-problem"></a>Sorunu açıkla

### <a name="describe_the_problem"></a>

1. Sorunu, Visual Studio içinde doğru ekibe yönlendirmemize yardımcı olacak açıklayıcı bir başlık verin.

2. Ek ayrıntılar ve mümkünse sorunu yeniden oluşturmak için gereken adımları verin.

3. Açılan listeden bir sorun alanı seçin. Emin değilseniz en iyi bir tahmin yapın.

   ![Sorun bildir Iletişim kutusu](../ide/media/report-a-problem-dialog.png "Sorun bildir Iletişim kutusu")

## <a name="provide-a-screenshot-optional"></a>Bir ekran görüntüsü sağlayın (isteğe bağlı)

Geçerli ekranınızı Microsoft 'a göndermek için **bir ekran görüntüsü Ekle** ' yi seçin. Araç görüntüyü kırpmanızı sağlar ve bu da sorunu gösteren ekranın yalnızca bir kısmını gösterir. Ek **Dosyalar Ekle** düğmesine tıklayarak ek ekran görüntüleri veya başka dosyalar ekleyebilirsiniz.

## <a name="provide-a-trace-and-heap-dump-optional"></a>İzleme ve yığın dökümü sağlama (isteğe bağlı)

### <a name="provide_a_trace_and_heap_dump"></a>

1. İzleme ve yığın dökümü dosyaları, sorunları tanılamamıza yardımcı olmak için çok yararlıdır.   Yeniden oluşturma adımlarınızı kaydetmek ve verileri Microsoft 'a göndermek için sorun bildir aracını kullandığınızda çok fazla teşekkür ederiz.

2. **Sorunu yeniden oluşturmak için eylemlerinizi kaydetmek**için yanındaki köşeli çift ayraca tıklayın. Sorununuz Visual Studio 'nun askıda kalmasına veya kilitlenmesine neden oluyorsa, Visual Studio 'nun başka bir örneğini açın ve liste görünümünden seçin.

3. **Kaydı Başlat** ' a tıklayın ve sorunu yeniden oluşturmak için adımları gerçekleştirin. İşiniz bittiğinde, kayan penceredeki **Kaydı Durdur** düğmesine tıklayın.

4. Visual Studio 'nun kaydedilen bilgileri toplaması ve paketlemeleri için birkaç dakika bekleyin. Toplama işlemi tamamlandığında iletişim kutusu şöyle görünür:

     ![Izleme dosyası kaydetme](../ide/media/record-a-trace-file.png "Izleme dosyası kaydetme")

## <a name="describe-the-workaround-if-there-is-one"></a>Varsa geçici çözümü açıkla

Sorunu geçici olarak çözebiliyorsanız, lütfen geçici çözümü bu amaçla sunulan düzenleme kutusunda tanıtın. Bu, yalnızca sorunu tanılamamıza yardımcı olur, ancak aynı sorunu yaşayan diğer kullanıcılara da yardımcı olabilir.

## <a name="submit-the-report"></a>Raporu gönder

Raporunuzu, herhangi bir görüntü ve izleme ya da döküm dosyası ile birlikte göndermek için Gönder düğmesine tıklayın. **Gönder** düğmesi gri ise, bir başlık ve açıklama girdiğinizden emin olun.

## <a name="see-also"></a>Ayrıca Bkz.

- [Bizimle İletişime Geçin](../ide/talk-to-us.md)
