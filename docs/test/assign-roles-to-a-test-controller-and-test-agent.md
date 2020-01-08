---
title: Otomatikleştirilmiş testler için test denetleyicisi ve test aracısı rolleri
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591196"
---
# <a name="assign-roles-to-a-test-controller-and-test-agent"></a>Bir test denetleyicisine ve test aracısına roller atama

Bu makalede, Visual Studio kullanarak çeşitli makinelerde test dağıtmak için test denetleyicisi ve test Aracısı kullanan bir test ayarı oluşturma ve yapılandırma gösterilmektedir. Ayrıca, test ayarına tanılama ve veri bağdaştırıcılarının nasıl ekleneceğini gösterir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="prerequisites"></a>Prerequisites

- Test ayarıyla çalıştırmak için birim testleri veya kodlanmış UI testleri oluşturun.

- Test denetleyicisi ve test aracıları yükler. Test denetleyicisi ve test aracılarının nasıl yükleneceği hakkında bilgi için bkz. [test aracılarını yüklemek ve yapılandırmak](../test/lab-management/install-configure-test-agents.md).

## <a name="to-create-and-configure-a-test-setting"></a>Bir test ayarı oluşturmak ve yapılandırmak için

1. **Çözüm Gezgini**, **Çözüm öğeleri** ' ne sağ tıklayın, **Ekle**' nin üzerine gelin ve sonra **Yeni öğe**' yi seçin.

     **Yeni Öğe Ekle** iletişim kutusu görüntülenir.

2. İçinde **yüklü şablonlar** bölmesinde seçin **Test ayarları**.

3. **Ad** kutusuna **TestSettingDistributedTestWalkthrough**yazın.

4. Seçin **ekleme**.

     Yeni test *TestSettingDistributedTestWalkthrough. testsettings* dosyası **Çözüm öğeleri** klasörü altında **Çözüm Gezgini**görüntülenir.

     **Test ayarları** iletişim kutusu görüntülenir. **Genel** sayfası seçili.

     Şimdi, düzenleme ve test ayarları değerlerini kaydedin.

5. Altında **adı**, test ayarları adını yazın.

6. **Açıklama**' nın altında, **Dağıtılmış test ayarları**yazın.

7. **Varsayılan adlandırma şemasını** seçili bırakın.

## <a name="to-assign-roles-to-a-test-controller-and-test-agents"></a>Bir test denetleyicisine ve Test aracılarına roller atamak için

1. Seçin **rolleri**.

     **Rolleri** sayfası görüntülenir.

2. Testinizi uzaktan çalıştırmak için **test yürütme yöntemi** açılan listesini kullanın ve **Uzaktan yürütme**' yi seçin.

3. **Denetleyici** açılan listesinde, [Test denetleyicinizin](../test/lab-management/install-configure-test-agents.md)bilgisayar adını yazın.

    > [!NOTE]
    > İlk kez bir denetleyici ekliyorsanız, açılan listede hiçbir denetleyici listelenmez. Liste diğer test ayarlarında belirttiğiniz önceki denetleyiciler tarafından doldurulur.

4. **Roller**altında **Ekle**' yi seçin.

5. **Ad** sütununun altındaki vurgulanmış satıra **Dağıtılmış test**yazın.

## <a name="to-assign-a-diagnostic-and-data-adapter-to-your-test-setting"></a>Test ayarınıza bir tanılama ve veri bağdaştırıcısı atamak için

1. Seçin **veri ve tanılama**.

     **Veri ve tanılama** sayfası görüntülenir.

2. **Rol**altında, **Dağıtılmış test** rolünün seçili olduğunu doğrulayın.

3. **Rol Seç Için veri ve tanılama**altında **IntelliTrace** ve **sistem bilgi** bağdaştırıcılarını seçin.

     Bir test ayarında kullanabileceğiniz bu bağdaştırıcılar ve diğer bağdaştırıcılar hakkında daha fazla bilgi için bkz. [birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

4. **Konaklar**' ı seçin.

5. Seçim Makineniz Microsoft Windows 'un 64 bitlik bir sürümü altında çalışıyorsa ve **herhangi BIR CPU** yapılandırmasını kullanarak testinizi derlediğiniz takdirde, test için **32 bit veya 64 bit işlem Çalıştır** açılan listesini kullanın ve 64-bit **makinede 64-bit işleminde Testleri Çalıştır**' ı seçin.

    > [!TIP]
    > En yüksek esneklik için, test projelerinizi **herhangi BIR CPU** yapılandırmasıyla derlemeniz gerekir. Daha sonra hem 32-bit hem de 64 bit aracıların çalıştırabilirsiniz. **64 bitlik** yapılandırma ile test projelerini derlemek avantajsız değildir.

6. Yeni test ayarlarını kaydetmek için **Uygula**' yı seçin.

7. Seçin **Kapat**.

::: moniker range="vs-2017"

8. **Test** menüsünde test **ayarları** ' nı seçin > **Test ayarları dosyasını seçin** ve ardından *TestSettingDistributedTestWalkthrough. testsettings* dosyasını seçin.

::: moniker-end

::: moniker range=">=vs-2019"

8. **Test** menüsünde, **ayarlar dosyası seç**' i seçin. *TestSettingDistributedTestWalkthrough. testsettings* dosyasına gidin ve seçin.

::: moniker-end

9. Testinizi her zamanki gibi çalıştırın.

     Test denetleyicisi birim testleri ve kodlanmış UI testlerini işlediğinde, test denetleyicisi testleri 100 gruplarına böler ve bunları bir test aracısı makinesine gönderir. Örneğin, 250 birim testiniz ve üç test aracınız varsa, ilk 100 birim testleri agent1 'e gönderilir, sonraki 100 birim testleri agent2 'e gönderilir ve kalan 50 birim testleri agent3 'e gönderilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)
