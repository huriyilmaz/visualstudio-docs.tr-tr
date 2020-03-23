---
title: Yük testi için Test Yinelemelerini Yapılandırma
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios, iterations
- load test, iterations
- load tests, scenarios
ms.assetid: ac480fb7-f4f7-47dc-9ae5-98be3aca4fba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e95ca27ace50c7b28d1ffb1d3fc02589daddee2d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590988"
---
# <a name="configure-test-iterations-in-a-load-test-scenario"></a>Yük testi senaryosunda test yinelemelerini yapılandırma

Test yineleme ayarlarını yapılandırmak için Yük Testi Düzenleyicisi ve **Özellikler** penceresini kullanarak bir yük testi senaryosu nu düzeltin. Varsayılan olarak, bir yük testi senaryosu maksimum test yinelemeleri belirtilmeden ayarlanır. Senaryodaki en fazla yineleme sayısını ve aralarında ne kadar süre duraklatma nızı yapılandırma seçeneğiniz vardır.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-maximum-test-iterations-for-a-scenario"></a>Bir senaryo için maksimum test yinelemelerini belirtin

**Özellikler** penceresindeki **Maksimum Test Yinelemeleri** özelliğini değiştirmek için Yük Testi Düzenleyicisi'ni kullanarak testlerinizin bir senaryo için çalışmasını istediğiniz maksimum kaç sayıbelirtebilirsiniz.

**Maksimum Test Yinelemeler** özelliği, senaryo için çalışacak maksimum test yineleme sayısını denetler. Yük testi çalıştırma ayarlarındaki **Test Yinelemeleri** özelliğinde olduğu gibi, bu da kullanıcı başına ayar değil, tüm aracılar üzerindeki tüm kullanıcılar arasında maksimum değerdir.

> [!NOTE]
> Yük testi senaryo özelliklerinin ve açıklamalarının tam listesi için [bkz.](../test/load-test-scenario-properties.md)

Sıralı test karışımı için, bir yineleme karışımı tüm testler aracılığıyla bir geçiştir. Diğer tüm test karışımları için, her test yürütme bir yineleme olarak sayar. Daha fazla bilgi için [karışım denetimi hakkında](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)bilgi.

Yük testi süre tabanlı bir yük testiyse ve yineleme sayısı tamamlanmadan önce süre sona eriyorsa, test yine de durdurulur. Test yineleme tabanlıysa ve test yinelemeleri senaryo yinelemesinden önce karşılanırsa, test durdurulür. Süre, bir yük testinde çalışma ayarı ile ilişkili **Özellikler** penceresindeki **Çalıştır Süresi** özelliği kullanılarak yapılandırılır.

Senaryo yineleme sayısı karşılandığında, senaryo çalışma durdurulacaktır, ancak diğer etkin senaryolar çalışmaya devam eder.

> [!NOTE]
> İlgili özellik, veriler arasında satır satır, ancak her kayıt için yalnızca bir kez sırayla hareket eden bir web test veri kaynağındaki **Benzersiz** özelliktir. Daha fazla bilgi için [bkz.](../test/add-a-data-source-to-a-web-performance-test.md)

**Maksimum Test Yinelemeleri** özelliği çeşitli durumlar için yararlıdır. Bazı yük test çileri yineleme tabanlı test yapmayı tercih ederken, diğer yük test çileri süre tabanlı test yapmayı tercih ediyor.

![Senaryoda test yinelemelerini belirtme](../test/media/loadtest_prop.png)

### <a name="to-specify-the-maximum-test-iterations"></a>Maksimum test yinelemelerini belirtmek için

1. Bir yük testi açın.

2. Yük Testi Düzenleyicisi görüntülenir. Yük testi ağacı görüntülenir.

3. Yük testi ağaçları **Senaryolar** klasöründe, en fazla test yinelemesayısını belirtmek istediğiniz senaryo düğümünü seçin.

4. **Görünüm** menüsünde **Özellikler Penceresi'ni**seçin.

     Senaryonun kategorileri ve özellikleri **Özellikler** penceresinde görüntülenir.

5. **Maksimum Test Yinelemeleri** özelliğinin metin kutusunda, yükleme testi çalıştırıldığında senaryo için çalışacak maksimum test sayısını gösteren bir değer yazın.

    > [!NOTE]
    > **Maksimum Test Yinelemeler** özelliği için 0 değeri kullanmak, maksimum yineleme ler belirtmezse.

6. Özelliği değiştirmeyi bitirdikten sonra **Dosya** menüsünde **Kaydet'i** seçin. Daha sonra yeni **Maksimum Test Yinelemeleri** değerini kullanarak yük testinizi çalıştırabilirsiniz.

## <a name="specify-think-times-between-test-iterations-for-a-scenario"></a>Bir senaryo için test yinelemeleri arasındaki düşünme sürelerini belirtin

**Test Yinelemeleri Arasındaki Düşünme Süresi** özelliği, Yük Testi Düzenleyicisi'ndeki yük testi senaryo özelliklerini düzenlerken **Özellikler** penceresi kullanılarak ayarlanır.

**Test Yinelemeleri Arasındaki Düşünme Süresi** özelliği, bir test yinelemesine başlamadan önce bekleyecek saniye miktarını belirtmek için kullanılır.

> [!NOTE]
> Yük testi senaryo özelliklerinin ve açıklamalarının tam listesi için [bkz.](../test/load-test-scenario-properties.md)

### <a name="to-specify-the-think-time-between-test-iterations"></a>Test yinelemeleri arasındaki düşünme süresini belirtmek için

1. Bir yük testi açın.

     **Yük Testi Düzenleyicisi** görüntülenir. Yük testi ağacı görüntülenir.

2. Yükleme testi ağaçları **Senaryolar** klasöründe, düşünme süresini belirtmek istediğiniz senaryo düğümünü seçin.

3. **Görünüm** menüsünde **Özellikler Penceresi'ni**seçin.

     Senaryonun kategorileri ve özellikleri **Özellikler** penceresinde görüntülenir.

4. **Test Yinelemeleri Arasındaki Zamanı Düşünme** özelliğine, bir sonraki test yinelemesini başlatmadan önce beklemek üzere saniye sayısını gösteren bir sayı girin.

5. Özelliği değiştirmeyi bitirdikten sonra **Dosya** menüsünde **Kaydet'i** seçin. Daha sonra yeni **Test Yinelemeleri Arasındaki Zaman** Değerini kullanarak yük testinizi çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)
- [Yük testleri için test aracılarını ve test denetleyicilerini yapılandırın](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Yük testi senaryo özellikleri](../test/load-test-scenario-properties.md)
- [Web sitesi insan etkileşimi gecikmeleri simüle etmek için düşünmek kez edin](../test/edit-think-times-in-load-test-scenarios.md)
