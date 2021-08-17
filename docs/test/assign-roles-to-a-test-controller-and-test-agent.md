---
title: Test denetleyicisi ve test aracısı rolleri
description: Test denetleyicisi ve test aracısı kullanan bir test ayarı oluşturma ve yapılandırma hakkında bilgi Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 1caf441e0dab8ef1216380dbc5d7bc8c1ec1b461
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038493"
---
# <a name="assign-roles-to-a-test-controller-and-test-agent"></a>Bir test denetleyicisine ve test aracısına rol atama

Bu makalede, test denetleyicisi ve test aracısı kullanan bir test ayarının nasıl oluşturularak yapılandırıldığında ve test aracısını kullanarak testlerin birden fazla makineye Visual Studio. Ayrıca test ayarına tanılama ve veri bağdaştırıcıları ekleme de gösterir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="prerequisites"></a>Önkoşullar

- Test ayarıyla çalıştırmak için birim testleri veya kodlanmış UI testleri oluşturun.

- Bir test denetleyicisi ve test aracıları yükleyin. Test denetleyicisini ve test aracılarını yükleme hakkında bilgi için bkz. Test [aracılarını yükleme ve yapılandırma.](../test/lab-management/install-configure-test-agents.md)

## <a name="to-create-and-configure-a-test-setting"></a>Test ayarı oluşturmak ve yapılandırmak için

1. Bu **Çözüm Gezgini,** Çözüm Öğeleri'ne **sağ tıklayın, Ekle'nin** üzerine **gelin** ve Yeni **Öğe'yi seçin.**

     **Yeni Öğe Ekle** iletişim kutusu görünür.

2. Yüklü **Şablonlar bölmesinde Test** şablonu'Ayarlar. 

3. Ad **kutusuna** **TestSettingDistributedTestWalkthrough yazın.**

4. **Ekle'yi seçin.**

     Yeni *testSettingDistributedTestWalkthrough.testsettings* **dosyası, Çözüm Gezgini** Öğeleri klasörünün **altında görüntülenir.**

     **Test Ayarlar** iletişim kutusu görüntülenir. Genel **sayfası** seçilidir.

     Artık test ayarları değerlerini düzenleyebilir ve kaydedebilirsiniz.

5. **Ad'ın** altına test ayarlarının adını yazın.

6. **Açıklama'nın** altında Dağıtılmış **test ayarları yazın.**

7. Varsayılan **adlandırma düzenini seçili** bırakın.

## <a name="to-assign-roles-to-a-test-controller-and-test-agents"></a>Bir test denetleyicisine ve test aracısına rol atamak için

1. **Roller'i seçin.**

     Roller  sayfası görüntülenir.

2. Testlerinizi uzaktan çalıştırmak için Test yürütme yöntemi **açılan** listesini kullanın ve Uzaktan **yürütme'yi seçin.**

3. Denetleyici **açılan** listesinde, test denetleyicinizin bilgisayar [adını yazın.](../test/lab-management/install-configure-test-agents.md)

    > [!NOTE]
    > Denetleyiciyi ilk kez ekliyorsanız, açılan listede hiçbir denetleyici listelenmiyor. Liste, diğer test ayarlarında belirttiğiniz önceki denetleyiciler tarafından doldurulur.

4. **Roller'in** altında Ekle'yi **seçin.**

5. Ad sütununu altındaki vurgulanan **satıra** Dağıtılmış **test yazın.**

## <a name="to-assign-a-diagnostic-and-data-adapter-to-your-test-setting"></a>Test ayarınıza tanılama ve veri bağdaştırıcısı atamak için

1. Veri **ve Tanılama'yı seçin.**

     **Veri ve Tanılama** sayfası görüntülenir.

2. Rol **altında** Dağıtılmış test **rolünün seçili** olduğunu doğrulayın.

3. Rol **seçin için Veri ve Tanılama altında** **IntelliTrace ve** Sistem Bilgileri seçin. 

     Bu bağdaştırıcılar ve bir test ayarında kullanabileceğiniz diğer bağdaştırıcılar hakkında bilgi için bkz. [Birim testlerini yapılandırma.](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)

4. **Konaklar'ı seçin.**

5. (İsteğe bağlı) Makineniz Microsoft Windows'nin 64 bit sürümü altında çalışıyorsa ve testini Herhangi bir **CPU** yapılandırması kullanarak derle yaptıysanız, Testi **32 bit veya 64 bit** işlemde çalıştır açılan listesini kullanın ve Testleri 64 bit makinede **64 bit** işlemde çalıştır'ı seçin.

    > [!TIP]
    > Maksimum esneklik için test projelerinizi Herhangi bir **CPU yapılandırmasıyla derlemeniz** gerekir. Ardından hem 32 bit hem de 64 bit aracılar üzerinde çalıştırarak. Test projelerini **64 bit** yapılandırmayla derlemenin bir avantajı yoktur.

6. Yeni test ayarlarını kaydetmek için Uygula'ya **tıklayın.**

7. **Kapat'ı seçin.**

::: moniker range="vs-2017"

8. Test menüsünde **Test**  Ayarlar Test Ayarlar'ı seçin ve >  *ardından TestSettingDistributedTestWalkthrough.testsettings dosyasını* seçin.

::: moniker-end

::: moniker range=">=vs-2019"

8. Test menüsünde **Dosya** **seç'i Ayarlar seçin.** *TestSettingDistributedTestWalkthrough.testsettings* dosyasına gidin ve dosyayı seçin.

::: moniker-end

9. Testlerinizi her zamanki gibi çalıştırın.

     Test denetleyicisi birim testlerini ve kodlanmış UI testlerini işleyene, test denetleyicisi testleri 100'lık gruplara böler ve bir test aracısı makinesine gönderir. Örneğin, 250 birim testi ve üç test aracınız varsa ilk 100 birim testi aracı1'e gönderilir, sonraki 100 birim testi aracı2'ye, kalan 50 birim testi de aracı3'e gönderilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)
