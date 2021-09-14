---
title: Testler sırasında ekran ve ses kaydetme
description: Visual Studio içinde testi çalıştıran kullanıcının ekranını ve sesini kaydeden tanılama veri bağdaştırıcısını nasıl yapılandıracağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- test settings, recording desktop video
ms.assetid: 2cefe8c2-430a-4cb4-bbe0-f3edb2e5bc03
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 3ccc9970c3e668a5242a5d409670da544d628992
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628118"
---
# <a name="how-to-include-recordings-of-the-screen-and-voice-during-tests-using-test-settings"></a>Nasıl yapılır: test ayarlarını kullanarak testler sırasında ekran ve ses kayıtlarını ekleme

Visual Studio içindeki yapılandırma düzenleyicisinden, testi çalıştıran kullanıcının ekranını ve sesini kaydeden tanılama veri bağdaştırıcısını yapılandırabilirsiniz. Bu tanılama veri bağdaştırıcısı, test sırasında Masaüstü oturumunun ekran ve ses kaydını kaydeder. Kayıt, test sonucuyla birlikte kaydedilir veya bir hataya eklenebilir. Diğer takım üyeleri, yeniden oluşturulması zor olan uygulama kusurlarını yalıtmak için kayıt kullanabilir.

> [!WARNING]
> Ekran ve ses kayıtları birden çok İzleyici yapılandırmasını desteklemez.

Ekran ve Ses Kaydedicisi, el ile veya otomatikleştirilmiş testlerle birlikte kullanılabilir. Örneğin, kodlanmış UI testini uzaktan çalıştırırsanız, kodlanmış UI testini çalışırken görmek için masaüstünü kaydetmek isteyebilirsiniz. Bir ekran ve ses kaydını uzaktan yakalama hakkında daha fazla bilgi için bkz. [nasıl yapılır: Masaüstü ile etkileşime sahip testleri çalıştırmak için test aracınızı ayarlama](../test/how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-configure-screen-and-voice-recording-for-your-test-settings"></a>Test ayarlarınıza yönelik ekran ve ses kaydını yapılandırmak için

1. Ekran ve ses kaydetmek için yapılandırmak istediğiniz test ayarlarını açın. daha fazla bilgi için bkz. test [sırasında tanılama verilerini toplama (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true) veya [test ayarlarını kullanarak tanılama bilgilerini toplama](../test/collect-diagnostic-information-using-test-settings.md).

2. Test ayarları ' nda, ekran ve ses kaydetmek için kullanılacak **rolü** seçin.

    > [!NOTE]
    > El ile testler ve otomatikleştirilmiş testler için, testleri çalıştıran makine olacaktır.

3. **ekran ve Ses Kaydedicisi** seçin ve ardından **yapılandır**' ı seçin.

     **tanılama veri bağdaştırıcısını yapılandır – ekran ve Ses Kaydedicisi** iletişim kutusu görüntülenir.

     ![Video yapılandırması](../test/media/testsettingvideoconfiggdr.png)

4. Seçim Kaydınıza ses içeriğini yakalamak için **Ses kaydını etkinleştir** ' i seçin.

5. Seçim Kayıt Kaydet ' in yanındaki onay kutusunu seçin ve **test çalışması,** hem başarısız hem de başarılı testler için kaydetme ekran ve ses kayıtlarını belirtin.

    > [!WARNING]
    > **Test çalışması geçerse kaydı kaydet**' i seçerseniz, kayıt, sunucuda depolama alanı kullanan test sonuçlarıyla depolanır. Bu ekleri temizlemek için **Test eki temizleyici** aracı 'nı kullanabilirsiniz.

6. **Ekran kayıt kalitesi** altında aşağıdaki açılan liste seçeneklerini yapılandırın:

    1. **Kare hızı:** Ekranda ve ses kaydında saniye başına kaç kare kullanmak istediğinizi belirtin. Varsayılan değer, saniye başına 4 kare olur. 2 ve 20 arasındaki değerler belirtilebilir.

    2. **Bit hızı:** Ekran ve ses kaydında saniye başına kaç kilobayt kullanılacağını belirtin. Varsayılan değer 512'dır. 512 ve 10.000 arasındaki değerler belirlenebilir.

    3. **Kalite (1-100):** 1 ile 100 arasında bir Aralık seçerek ekran ve ses kaydı kalitesini belirtebilirsiniz. Varsayılan değer 50 ' dir (orta Aralık).

7. **Tamam ' ı** seçin. Tanılama izleme toplayıcısı ayarları artık test ayarlarınız için yapılandırılır ve kaydedilir.

    ::: moniker range="vs-2017"
    > [!TIP]
    > bu tanılama veri bağdaştırıcısı için yapılandırmayı sıfırlamak üzere Visual Studio için **varsayılan yapılandırmaya sıfırla** ' yı seçin ve Microsoft Test Yöneticisi için varsayılana **sıfırlayın** .
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    > [!TIP]
    > Bu tanılama veri bağdaştırıcısı için yapılandırmayı sıfırlamak üzere Visual Studio ' de **varsayılan yapılandırmaya Sıfırla** ' yı seçin.
    ::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Test sırasında tanılama verilerini topla (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true)
- [Tanılama verilerini el ile testlerde topla (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true)
- [Test ayarlarını kullanarak tanılama bilgilerini topla](../test/collect-diagnostic-information-using-test-settings.md)
- [El ile testleri çalıştırma (Azure Test Plans)](/azure/devops/test/run-manual-tests?view=vsts&preserve-view=true)