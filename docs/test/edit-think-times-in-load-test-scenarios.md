---
title: Yük testi için Düşünme Süreleri
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, think times
- load tests, adding delays
- load tests, changing think times
ms.assetid: 8e03bee5-ab7b-4b40-9497-9dbe91ccb90e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 887d2af9e60be914bd74141041ecc375cfea4f00
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590039"
---
# <a name="edit-think-times-to-simulate-website-human-interaction-delays-in-load-tests-scenarios"></a>Yük testleri senaryolarında web sitesi insan etkileşimi gecikmeleri simüle etmek için düşünme sürelerini edin

Düşünme süreleri, insanların bir web sitesi yle etkileşimleri arasında beklemelerine neden olan insan davranışlarını simüle etmek için kullanılır. Web performans testindeki istekler ile yük testi senaryosundaki test yinelemeleri arasında düşünme süreleri oluşur. Bir yük testinde düşünme sürelerini kullanmak, daha doğru yük simülasyonları oluşturmada yararlı olabilir. Düşünme süreleri yük testlerinde kullanılıp kullanılmadığını veya göz ardı edilip edilmeyeceğini değiştirebilirsiniz. Yük Testi Düzenleyicisi'ndeki yükleme testlerinizde düşünme sürelerinin kullanılıp kullanılmayacağını değiştirirsiniz. **Load Test Editor**

*Düşünme profili,* yük testindeki bir senaryo için geçerli olan bir ayardır. Ayar, tek tek web performans testlerinde kaydedilen düşünme sürelerinin yük testi sırasında kullanılıp kullanılmayacağını belirler. Bazı web performans testlerinde düşünme sürelerini kullanmak, ancak diğerlerinde değil, bunları farklı senaryolara yerleştirmeniz gerekir. Senaryolar hakkında daha fazla bilgi için [bkz.](../test/edit-load-test-scenarios.md)

Başlangıçta, **Yeni Yük Testi Sihirbazı'nı**kullanarak yük testini oluştururken yük testlerinizde düşünme sürelerini kullanıp kullanmadığınızı ayarlarsınız. Daha fazla bilgi için [bkz.](../test/edit-load-test-scenarios.md)

**Think Profile** seçenekleri aşağıdaki listede açıklanmıştır:

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Kapalı**

Düşünme süreleri göz ardı edilir. Web sunucunuzu ağır bir şekilde strese koymak için maksimum yük oluşturmak istediğinizde bu ayarı kullanın. Bir web sunucusu ile daha gerçekçi kullanıcı etkileşimleri oluşturmaya çalışırken kullanmayın.

**Açık**

Düşünme süreleri tam olarak web performans testinde kaydedildikleri gibi kullanılır. Web performans testlerini tam olarak kaydedildikçe çalıştıran birden çok kullanıcıyı simüle eder. Bir yük testi birden çok kullanıcıyı simüle ettiği için, aynı düşünme süresini kullanmak, senkronize edilmiş sanal kullanıcıların doğal olmayan bir yük deseni oluşturabilir.

**Normal Dağılım**

Düşünme süreleri kullanılır, ancak normal bir eğri üzerinde değişir. İstekler arasındaki düşünme süresini biraz değiştirerek sanal kullanıcıların daha gerçekçi bir simülasyonu sağlar.

> [!NOTE]
> Yük testi senaryo özelliklerinin ve açıklamalarının tam listesi için [bkz.](../test/load-test-scenario-properties.md)

## <a name="change-the-think-profile"></a>Düşünme profilini değiştirme

### <a name="to-change-a-think-profile-in-a-load-test-scenario"></a>Yük testi senaryosunda düşünme profilini değiştirmek için

1. Web performansı ve yük testi projesinden bir yük testi açın.

2. Load **Test**Editor'da, **Think Profilini**değiştirmek istediğiniz senaryo düğümünü seçin. Özellikler **penceresinde** **Think Profili** görüntülenir. **Özellikler** penceresini görüntülemek için **F4** tuşuna basın.

3. **Özellikler** penceresindeki **Think Profile** özelliğini değiştirin.

4. Özellikleri değiştirmeyi bitirdikten sonra **Dosya** menüsünde **Kaydet'i** seçin. Daha sonra yeni düşünme profili ile yük testi çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını edin](../test/edit-load-test-scenarios.md)
