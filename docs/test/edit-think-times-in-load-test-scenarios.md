---
title: Yük testi için Düşünme Süreleri
description: İnsanların bir web sitesiyle etkileşimler arasında beklemesi için neden olan insan davranışlarının benzetimini yapmak için düşünme sürelerini düzenlemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, think times
- load tests, adding delays
- load tests, changing think times
ms.assetid: 8e03bee5-ab7b-4b40-9497-9dbe91ccb90e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: cc11872aa238ee1b3b72a171193de6b7d0ee972b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148603"
---
# <a name="edit-think-times-to-simulate-website-human-interaction-delays-in-load-tests-scenarios"></a>Yük testi senaryolarında web sitesi insan etkileşimi gecikmelerinin benzetimini yapmak için düşünme sürelerini düzenleme

Düşünme süreleri, insanların bir web sitesiyle etkileşimler arasında beklemelerini neden olan insan davranışlarının benzetimini yapmak için kullanılır. Bir web performans testinde istekler ile yük testi senaryosunda test yinelemeleri arasında oluşan zamanları düşünün. Yük testinde düşünme sürelerini kullanmak, daha doğru yük simülasyonları oluşturmada yararlı olabilir. Yük testlerinde düşünme zamanların kullan mı yoksay mı olduğunu değiştirebilirsiniz. 'de yük testlerinde düşünme zamanlarını kullanıp **Yük Testi Düzenleyicisi.**

Düşünme *profili,* yük testinde senaryo için geçerli olan bir ayardır. ayarı, tek tek web performans testlerinde kaydedilen düşünme sürelerinin yük testi sırasında kullanıp kullanılmadığını belirler. Bazı web performans testlerinde düşünme sürelerini kullanmak ancak diğer testlerde kullanmak istemiyorsanız, bunları farklı senaryolara yer edin. Senaryolar hakkında daha fazla bilgi için [bkz. Yük testi senaryolarını düzenleme.](../test/edit-load-test-scenarios.md)

Başlangıçta, New Yük Testi Sihirbazı kullanarak yük testlerinizi yük testlerinizi oluşturmak için düşünme **zamanlarını kullanıp Yük Testi Sihirbazı.** Daha fazla bilgi için [bkz. Yük testi senaryolarını düzenleme.](../test/edit-load-test-scenarios.md)

Profili **Düşün** seçenekleri aşağıdaki listede açıklanmıştır:

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Kapalı**

Düşünme süreleri yoksayılır. Web sunucunuzda yoğun baskı oluşturmak için maksimum yük oluşturmak istediğinizde bu ayarı kullanın. Bir web sunucusuyla daha gerçekçi kullanıcı etkileşimleri oluşturmak için bunu kullanmayın.

**Açık**

Düşünme süreleri, web performans testinde kaydedildikleri gibi kullanılır. Web performans testlerini tam olarak kaydedilen şekilde çalıştıran birden çok kullanıcının benzetimini sağlar. Yük testi birden çok kullanıcının benzetimini lar, aynı düşünme zamanlarını kullanarak eşitlenen sanal kullanıcıların doğal olmayan bir yük deseni oluşturabilir.

**Normal Dağıtım**

Düşünme süreleri kullanılır, ancak normal bir eğri üzerinde çeşitlidir. İstekler arasındaki düşünme süresi biraz değişiklik göstererek sanal kullanıcıların daha gerçekçi bir simülasyonunu sağlar.

> [!NOTE]
> Yük testi senaryosu özelliklerinin ve açıklamalarının tam listesi için bkz. [Yük testi senaryosu özellikleri.](../test/load-test-scenario-properties.md)

## <a name="change-the-think-profile"></a>Düşünme profilini değiştirme

### <a name="to-change-a-think-profile-in-a-load-test-scenario"></a>Yük testi senaryosunda bir düşünme profilini değiştirmek için

1. Web performansı ve yük testi projesinde bir yük testi açın.

2. Bu **Yük Testi Düzenleyicisi,** Düşünme Profilini değiştirmek istediğiniz senaryo **düğümünü seçin.** Düşün **Profili** Özellikler **penceresinde** görüntülenir. Özellikler penceresini görüntülemek için **F4** **tuşuna** basın.

3. Özellikler **penceresinde Düşünme** Profili **özelliğini** değiştirin.

4. Özellikleri değiştirmeyi bitirdikten sonra Dosya menüsünde **Kaydet'i** seçin.  Daha sonra yük testini yeni düşünme profiliyle çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)
