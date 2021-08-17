---
title: Yük testi için test yinelemeleri yapılandırma
description: Test yineleme ayarlarını yapılandırmayı, senaryodaki en fazla yineleme sayısını ve bunlar arasında ne kadar duraklama gerektiğini yapılandırmak hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, scenarios, iterations
- load test, iterations
- load tests, scenarios
ms.assetid: ac480fb7-f4f7-47dc-9ae5-98be3aca4fba
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 0b6a32d49471b0adc3480bcb53455740204e1059b82bcb056f474b6df47c4cbc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121395400"
---
# <a name="configure-test-iterations-in-a-load-test-scenario"></a>Yük testi senaryosunda test yinelemelerini yapılandırma

Test yineleme ayarlarını yapılandırmak için, Yük Testi Düzenleyicisi ve **Özellikler** penceresini kullanarak bir yük testi senaryosunu düzenleyin. Varsayılan olarak, bir yük testi senaryosu en fazla test yinelemesi belirtilmeden ayarlanır. Senaryoda en fazla yineleme sayısını ve bunların arasında ne kadar duraklama gerektiğini yapılandırma seçeneğiniz vardır.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-maximum-test-iterations-for-a-scenario"></a>Bir senaryo için en fazla test yinelemesi belirleme

**Özellikler** penceresindeki **Maksimum test yinelemeleri** özelliğini değiştirmek için Yük Testi Düzenleyicisi kullanarak testlerinizin bir senaryo için kaç kez çalışacağını belirtebilirsiniz.

**Maksimum test yinelemeleri** özelliği, senaryo için çalıştırılacak en fazla test yinelemesi sayısını denetler. Yük testi çalıştırma ayarlarındaki **test yinelemeleri** özelliğinin olduğu gibi, bu, her kullanıcı için değil, tüm aracılarda bulunan tüm kullanıcılar arasında en yüksek değer olacaktır.

> [!NOTE]
> Yük testi senaryosu özelliklerinin tam listesi ve açıklamaları için bkz. [Yük testi senaryo özellikleri](../test/load-test-scenario-properties.md).

Sıralı test karışımı için, bir yineleme, karışımdaki tüm testlerin bir geçiştir. Tüm diğer test karışımları için, her test yürütmesi yineleme olarak sayılır. Daha fazla bilgi için bkz. [karışım denetimi hakkında](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

Yük testi Duration tabanlı bir yük testi ise ve süre süresi yineleme sayısı tamamlanmadan önce dolarsa, test durmaya devam eder. Test yineleme tabanlıdır ve test yinelemeleri senaryo yinelemeden önce karşılanıyorsa, test durur. Süre, yük testinde bir çalıştırma ayarıyla ilişkili **Özellikler** penceresindeki **çalışma süresi** özelliği kullanılarak yapılandırılır.

Senaryo yineleme sayısı karşılandığında, senaryo çalışmayı durdurur, ancak diğer etkin senaryolar çalışmaya devam eder.

> [!NOTE]
> İlgili bir özellik, bir Web testi veri kaynağı üzerindeki **benzersiz** bir özelliktir. Bu, veri, satır satır, ancak her bir kayıt için yalnızca bir kez sırayla taşınarak. Daha fazla bilgi için bkz. [Web performans testine veri kaynağı ekleme](../test/add-a-data-source-to-a-web-performance-test.md).

**En yüksek test yinelemeleri** özelliği, çeşitli durumlar için faydalıdır. Bazı yük Sınayıcılar yineleme tabanlı test yapmayı tercih eder, diğer yük Sınayıcılar süre tabanlı test yapmak için tercih eder.

![Bir senaryoda test yinelemeleri belirtme](../test/media/loadtest_prop.png)

### <a name="to-specify-the-maximum-test-iterations"></a>En yüksek test yinelemeleri belirtmek için

1. Bir yük testi açın.

2. Yük Testi Düzenleyicisi görüntülenir. Yük testi ağacı görüntülenir.

3. Yük testi ağaçları **senaryolar** klasöründe, en fazla test yinelemesi sayısını belirtmek istediğiniz senaryo düğümünü seçin.

4. **Görünüm** menüsünde **Özellikler penceresi**' ni seçin.

     Senaryonun kategorileri ve özellikleri **Özellikler** penceresinde görüntülenir.

5. **En yüksek test yinelemeleri** özelliğinin metin kutusunda, yük testi çalıştırıldığında senaryo için çalıştırılacak maksimum test sayısını belirten bir değer yazın.

    > [!NOTE]
    > **Maksimum test yinelemeleri** özelliği için 0 değeri kullanılması en fazla yineleme olmadığını belirtir.

6. Özelliği değiştirmeyi bitirdikten sonra **Dosya** menüsünde **Kaydet** ' i seçin. Daha sonra, yeni **en yüksek test yinelemeleri** değerini kullanarak yük testinizi çalıştırabilirsiniz.

## <a name="specify-think-times-between-test-iterations-for-a-scenario"></a>Senaryo için test yinelemeleri arasında düşünme süreleri belirtme

**Test Yinelemeleri özelliği arasındaki düşünme süresi** , Yük Testi Düzenleyicisi yük testi senaryosu özellikleri düzenlenirken **Özellikler** penceresi kullanılarak ayarlanır.

Test **Yinelemeleri özelliği arasındaki düşünme süresi** , bir test yinelemesi başlatılmadan önce beklenecek saniye miktarını belirtmek için kullanılır.

> [!NOTE]
> Yük testi senaryosu özelliklerinin ve açıklamalarının tüm listesi için bkz. [Yük testi senaryo özellikleri](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-think-time-between-test-iterations"></a>Test yinelemeleri arasındaki düşünme süresini belirtmek için

1. Bir yük testi açın.

     **Yük Testi Düzenleyicisi** görüntülenir. Yük testi ağacı görüntülenir.

2. Yük testi ağaçları **senaryolar** klasöründe, düşünme süresini belirtmek istediğiniz senaryo düğümünü seçin.

3. **Görünüm** menüsünde **Özellikler penceresi**' ni seçin.

     Senaryonun kategorileri ve özellikleri **Özellikler** penceresinde görüntülenir.

4. **Test Yinelemeleri özelliği arasındaki düşünme süresi** değeri için, sonraki test yinelemesine başlamadan önce beklenecek saniye sayısını gösteren bir sayı girin.

5. Özelliği değiştirmeyi bitirdikten sonra **Dosya** menüsünde **Kaydet** ' i seçin. Ardından, **test yinelemeleri değeri arasındaki yeni düşünme süresini** kullanarak yük testinizi çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleniyor](../test/edit-load-test-scenarios.md)
- [Yük testleri için test aracılarını ve test denetleyicilerini yapılandırma](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)
- [Web sitesi insan etkileşimi gecikmelerini benzetmek için düşünme zamanlarını düzenleme](../test/edit-think-times-in-load-test-scenarios.md)
