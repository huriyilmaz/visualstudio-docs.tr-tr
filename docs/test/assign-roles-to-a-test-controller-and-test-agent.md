---
title: Otomatik testler için test denetleyicisi ve test aracısı rolleri
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- testing, walkthroughs, test controller and test agents
- test agent, walkthrough
- walkthroughs [Visual Studio ALM] testing
- test controller, walkthrough
- walkthroughs, test controller and test agents
ms.assetid: 57ed43ae-4e67-4139-8aec-3e9fceb0a745
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f0ea644294ea79f1e4c044c0cebf3f427f5b672a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591196"
---
# <a name="assign-roles-to-a-test-controller-and-test-agent"></a>Bir test denetleyicisine ve test aracısına rol atama

Bu makalede, Visual Studio kullanarak çeşitli makineler arasında test dağıtmak için bir test denetleyicisi ve test aracısı kullanan bir test ayarı oluşturmak ve yapılandırmak nasıl gösterin. Ayrıca, tanılama ve veri bağdaştırıcılarının test ayarına nasıl ekleyeceğini de gösterir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="prerequisites"></a>Önkoşullar

- Test ayarı ile çalışmak için birim testleri veya kodlanmış UI testleri oluşturun.

- Bir test denetleyicisi ve test aracıları yükleyin. Test denetleyicisi ve test aracıları nasıl yüklenir hakkında bilgi için, [test aracılarını yükle ve yapılandırma](../test/lab-management/install-configure-test-agents.md)ya da yapılandırma'ya bakın.

## <a name="to-create-and-configure-a-test-setting"></a>Test ayarı oluşturmak ve yapılandırmak için

1. **Çözüm Gezgini'nde,** Çözüm Öğeleri'ni sağ **tıklatın,** **Ekle'ye**işaret edin ve ardından **Yeni Öğe'yi**seçin.

     **Yeni Öğe Ekle** iletişim kutusu görünür.

2. Yüklü **Şablonlar** **bölmesinde, Test Ayarları'nı**seçin.

3. **Ad** kutusunda **TestSettingDistributedTestWalkthrough**yazın.

4. **Ekle'yi**seçin.

     Yeni *test TestSettingDistributedTestWalkthrough.testsettings* dosyası **Çözüm Gezgini'nde**, **Çözüm Öğeleri** klasörü altında görünür.

     **Test Ayarları** iletişim kutusu görüntülenir. **Genel** sayfa seçilir.

     Artık test ayarları değerlerini disep kaydedebilirsiniz.

5. **Ad**altında, test ayarları için adı yazın.

6. **Açıklama**altında , **Dağıtılmış test ayarlarını**yazın.

7. **Varsayılan adlandırma düzenini** seçili bırakın.

## <a name="to-assign-roles-to-a-test-controller-and-test-agents"></a>Bir test denetleyicisine ve test aracılarına rol atamak için

1. **Rolleri**Seçin.

     **Roller** sayfası görüntülenir.

2. Testinizi uzaktan çalıştırmak **için, Test yürütme açılır listesini** kullanın ve Uzaktan **yürütmeyi**seçin.

3. **Denetleyici** açılır listesinde, [test denetleyicinizin](../test/lab-management/install-configure-test-agents.md)bilgisayar adını yazın.

    > [!NOTE]
    > Bu, ilk kez bir denetleyici eklediğiniz zaman, açılan listede listelenen denetleyiciler yoktur. Liste, diğer test ayarlarında belirttiğiniz önceki denetleyiciler tarafından doldurulur.

4. **Roller**altında **Ekle'yi**seçin.

5. **Ad** sütunu altında vurgulanan satırda **Dağıtılmış testi**yazın.

## <a name="to-assign-a-diagnostic-and-data-adapter-to-your-test-setting"></a>Test ayarınız için tanılama ve veri bağdaştırıcısı atamak için

1. **Veri ve Tanılama'yı**seçin.

     **Veri ve Tanılama** sayfası görüntülenir.

2. **Role**altında, **Dağıtılmış test** rolünün seçildiğini doğrulayın.

3. **Seçili rol için Veri ve Tanılama**altında, **IntelliTrace** ve **Sistem Bilgileri** bağdaştırıcılarını seçin.

     Bu bağdaştırıcılar ve test ayarında kullanabileceğiniz diğer bağdaştırıcılar hakkında bilgi için [yapı birimi testlerine](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)bakın.

4. **Ana Bilgisayar'ı**seçin.

5. (İsteğe bağlı) Makineniz Microsoft Windows'un 64 bit sürümü altında çalışıyorsa ve **herhangi** bir CPU yapılandırmasını kullanarak testinizi derlediyseniz, **32 bit veya 64 bit işlem** açılır listesinde Çalıştır testini kullanın ve **64 bit makinede 64 bit işlemde testleri çalıştır'ı**seçin.

    > [!TIP]
    > Maksimum esneklik için, test projelerinizi Herhangi **bir CPU** yapılandırması ile derlemeniz gerekir. Daha sonra hem 32 bit hem de 64 bit aracılar üzerinde çalıştırabilirsiniz. Test projelerini **64 bit** yapılandırma ile derlemenin bir avantajı yoktur.

6. Yeni test ayarlarını kaydetmek için **Uygula'yı**seçin.

7. **Kapat'ı**seçin.

::: moniker range="vs-2017"

8. **Test** menüsünde **Test Ayarları** > **Seç Test Ayarları Dosyasını** seçin ve ardından *TestSettingDistributedTestWalkthrough.test settings* dosyasını seçin.

::: moniker-end

::: moniker range=">=vs-2019"

8. **Test** menüsünde **Ayarlar Dosyasını Seç'i**seçin. *TestSettingDistributedTestWalkthrough.testsettings* dosyasına göz atın ve seçin.

::: moniker-end

9. Testi her zamanki gibi çalıştır.

     Test denetleyicisi birim testlerini ve kodlu UI testlerini işlediğinde, test denetleyicisi testleri 100'lü gruplara böler ve bunları bir test aracısı makinesine gönderir. Örneğin, 250 birim testiniz ve üç test aracınız varsa, ilk 100 birim testleri agent1'e, sonraki 100 birim testleri agent2'ye gönderilir ve kalan 50 birim testleri agent3'e gönderilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)
