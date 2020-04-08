---
title: Testler Sırasında Ekran ve Ses Kaydı
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, recording desktop video
ms.assetid: 2cefe8c2-430a-4cb4-bbe0-f3edb2e5bc03
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d53f03ed711b613a44aaf7cd243bd9aadeb2c93b
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880331"
---
# <a name="how-to-include-recordings-of-the-screen-and-voice-during-tests-using-test-settings"></a>Nasıl yapılır: Test ayarlarını kullanarak test sırasında ekran ve ses kayıtlarını ekleme

Visual Studio'daki yapılandırma düzenleyicisinden, testi çalıştıran kullanıcının ekranını ve sesini kaydeden tanılama veri bağdaştırıcısını yapılandırabilirsiniz. Bu tanılama veri bağdaştırıcısı, test sırasında masaüstü oturumunun ekran ve ses kaydını kaydeder. Kayıt test sonucu ile kaydedilir veya bir hata eklenebilir. Diğer ekip üyeleri, yeniden oluşturulması zor olan uygulama hatalarını yalıtmak için kaydı kullanabilir.

> [!WARNING]
> Ekran ve ses kayıtları birden çok monitör yapılandırmasını desteklemez.

Ekran ve ses kaydedici manuel veya otomatik testler ile kullanılabilir. Örneğin, kodlanmış bir UI testini uzaktan çalıştırdıysanız, masaüstünü kaydederken kodlanmış UI testini çalıştırmak isteyebilirsiniz. Ekran ve ses kaydının uzaktan nasıl yakalayacağı hakkında daha fazla bilgi için [bkz.](../test/how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop.md)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-configure-screen-and-voice-recording-for-your-test-settings"></a>Test ayarlarınız için ekran ve ses kaydını yapılandırmak için

1. Ekranı ve sesi kaydetmek için yapılandırmak istediğiniz test ayarlarını açın. Daha fazla bilgi için bkz: [Test ederken tanı verilerini topla (Azure Test Planları)](/azure/devops/test/collect-diagnostic-data?view=vsts) veya test [ayarlarını kullanarak tanı bilgilerini topla.](../test/collect-diagnostic-information-using-test-settings.md)

2. Test ayarlarında, ekranı ve sesi kaydetmek için kullanılacak **Rolü** seçin.

    > [!NOTE]
    > Manuel testler ve otomatik testler için bu testleri çalıştıran makine olacaktır.

3. **Ekran ve Ses Kaydedici'yi** seçin ve sonra **Yapıla'yı**seçin.

     **Yapılaşı Tanılama Veri Bağdaştırıcısı – Ekran ve Ses Kaydedici** iletişim kutusu görüntülenir.

     ![Video yapılandırması](../test/media/testsettingvideoconfiggdr.png)

4. (İsteğe bağlı) Kaydınızdaki ses içeriğini yakalamak için **ses kaydını etkinleştir'i** seçin.

5. (İsteğe bağlı) Hem başarısız hem de geçmiş testler için kaydetme ekranı ve ses kayıtları belirtmek için **test çalışması geçerse kaydı kaydet'in** yanındaki onay kutusunu seçin.

    > [!WARNING]
    > **Test çalışması geçerse kaydet kaydını**seçerseniz, kayıt sunucuda depolama alanı kullanan test sonuçlarıyla birlikte depolanır. Bu ekleri temizlemek için **Test Eki Temizleyici** aracını kullanabilirsiniz.

6. **Ekran Kayıt Kalitesi**altında, aşağıdaki açılır liste seçeneklerini yapılandırın:

    1. **Kare hızı:** Ekranda ve ses kaydında saniyede kaç kare kullanmak istediğinizi belirtin. Varsayılan değer saniyede 4 karedir. 2 ile 20 arasındaki değerler belirtilebilir.

    2. **Bit hızı:** Ekranda ve ses kaydında saniyede kaç kilobayt kullanılacağını belirtin. Varsayılan değer 512'dır. 512 ile 10.000 arasındaki değerler belirtilebilir.

    3. **Kalite(1-100):** 1 ile 100 arasında bir aralık seçerek ekran ve ses kaydının kalitesini belirtebilirsiniz. Varsayılan değer 50 'dir (orta sınıf).

7. **Tamam'ı**seçin. Tanılama izleme toplayıcı ayarları artık yapılandırılır ve test ayarlarınız için kaydedilir.

    ::: moniker range="vs-2017"
    > [!TIP]
    > Bu tanılama veri bağdaştırıcısının yapılandırmasını sıfırlamak için Visual Studio için **varsayılan yapılandırmaya sıfırla'yı** ve Microsoft Test Yöneticisi için **varsayılan olarak sıfırla'yı** seçin.
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    > [!TIP]
    > Bu tanılama veri bağdaştırıcısının yapılandırmasını sıfırlamak için Visual Studio'da **varsayılan yapılandırmaya sıfırla'yı** seçin.
    ::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Test ederken tanılama verileri toplama (Azure Test Planları)](/azure/devops/test/collect-diagnostic-data?view=vsts)
- [El ile yapılan testlerde tanılama verileri toplama (Azure Test Planları)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)
- [Test ayarlarını kullanarak tanılama bilgilerini toplama](../test/collect-diagnostic-information-using-test-settings.md)
- [El ile testler çalıştırın (Azure Test Planları)](/azure/devops/test/run-manual-tests?view=vsts)
