---
title: Testler Sırasında Kayıt Ekranı ve Ses
description: Test çalıştırılan kullanıcının ekran ve sesini kaydeden tanılama veri bağdaştırıcısını yapılandırmayı Visual Studio.
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
ms.openlocfilehash: 491980165ec7528ed111a3ec99eab79e656ecfda597c79b17dbc37e36d9fa1e7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121366646"
---
# <a name="how-to-include-recordings-of-the-screen-and-voice-during-tests-using-test-settings"></a>Nasıl kullanılır: Test ayarlarını kullanarak testler sırasında ekran ve ses kayıtlarını dahil edin

Visual Studio'daki yapılandırma düzenleyicisinden, testi çalıştıran kullanıcının ekranı ve sesini kaydeden tanılama veri bağdaştırıcısını yapılandırabilirsiniz. Bu tanılama veri bağdaştırıcısı, test sırasında masaüstü oturumunun ekran ve ses kaydını kaydeder. Kayıt test sonucuyla kaydedilir veya bir hataya iliştirilebilir. Diğer ekip üyeleri kaydı kullanarak yeniden oluşturması zor olan uygulama hatalarını yalıtılabilir.

> [!WARNING]
> Ekran ve ses kayıtları birden çok izleyici yapılandırması desteklemez.

Ekran ve ses kaydedici el ile veya otomatikleştirilmiş testlerle kullanılabilir. Örneğin, uzaktan kodlanmış ui testi çalıştırırsanız, çalışan kodlanmış UI testini görmek için masaüstünü kaydetmek iyi olabilir. Ekran ve ses kaydını uzaktan yakalama hakkında daha fazla bilgi için bkz. Nasıl kullanılır: Test aracınızı masaüstü ile etkileşimde bulunacak [testleri çalıştıracak şekilde ayarlama.](../test/how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop.md)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-configure-screen-and-voice-recording-for-your-test-settings"></a>Test ayarlarınız için ekran ve ses kaydını yapılandırmak için

1. Ekranı ve sesi kaydederken yapılandırmak istediğiniz test ayarlarını açın. Daha fazla bilgi için [bkz. Test sırasında tanılama verilerini toplama (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true) veya Test ayarlarını [kullanarak tanılama bilgilerini toplama.](../test/collect-diagnostic-information-using-test-settings.md)

2. Test ayarlarında, ekranı ve **sesi kaydetmek** için kullanmak istediğiniz Rolü seçin.

    > [!NOTE]
    > El ile yapılan testler ve otomatikleştirilmiş testler için bu, testleri çalıştıran makinedir.

3. Ekran **ve Ekran'Ses Kaydedicisi** ve ardından Yapılandır'ı **seçin.**

     Tanılama **Veri Bağdaştırıcısını Yapılandır – Ekran ve Ses Kaydedicisi** iletişim kutusu görüntülenir.

     ![Video yapılandırması](../test/media/testsettingvideoconfiggdr.png)

4. (İsteğe bağlı) Kaydınıza **ses içeriği yakalamak** için Ses kaydını etkinleştir'i seçin.

5. (İsteğe bağlı) Hem başarısız hem de başarılı testler için kayıt ekranı ve ses kayıtlarını belirtmek için **test** çalışması başarılı olursa Kaydı kaydet'in yanındaki onay kutusunu seçin.

    > [!WARNING]
    > Test çalışması **başarılı olursa kaydı kaydet'i seçmeniz** durumunda kayıt, sunucu üzerinde depolama alanı kullanan test sonuçlarıyla birlikte depolanır. Bu ekleri **temizlemek için Test** Eki Temizleme aracını kullanabilirsiniz.

6. Ekran **Kaydı Kalitesi altında** aşağıdaki açılan liste seçeneklerini yapılandırabilirsiniz:

    1. **Kare hızı:** Ekranda ve ses kaydında saniyede kaç kare kullanmak istediğinizi belirtin. Varsayılan değer saniyede 4 karedir. 2 ile 20 arasındaki değerler belirtilebilir.

    2. **Bit hızı:** Ekranda ve ses kaydında kaç kilobayt/saniye kullanıcazı belirtin. Varsayılan değer 512'dır. 512 ile 10.000 arasındaki değerler belirtilebilir.

    3. **Kalite(1-100):** 1 ile 100 arasında bir aralık seçerek ekranın ve ses kaydının kalitesini belirtebilirsiniz. Varsayılan değer 50'dir (orta aralık).

7. **Tamam'ı seçin.** Tanılama izleme toplayıcı ayarları artık yapılandırıldı ve test ayarlarınız için kaydedildi.

    ::: moniker range="vs-2017"
    > [!TIP]
    > Bu tanılama veri bağdaştırıcısının yapılandırmasını  sıfırlamak için Visual Studio için  varsayılan yapılandırmaya sıfırla'Microsoft Test Yöneticisi.
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    > [!TIP]
    > Bu tanılama veri bağdaştırıcısının yapılandırmasını sıfırlamak için Bu tanılama veri **bağdaştırıcısında varsayılan yapılandırmaya** sıfırla'Visual Studio.
    ::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Test sırasında tanılama verilerini toplama (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true)
- [Tanılama verilerini el ile yapılan testlerde toplama (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true)
- [Test ayarlarını kullanarak tanılama bilgilerini toplama](../test/collect-diagnostic-information-using-test-settings.md)
- [El ile testler çalıştırma (Azure Test Plans)](/azure/devops/test/run-manual-tests?view=vsts&preserve-view=true)