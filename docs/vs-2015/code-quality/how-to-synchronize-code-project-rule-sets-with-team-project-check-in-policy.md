---
title: 'Nasıl yapılır: takım projesi Iade Ilkesiyle kod proje kural kümelerini senkronize etme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3c6e7550940f9d2efa5ca228123310f1b861ee76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651593"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy"></a>Nasıl yapılır: Takım Projesi İade İlkesiyle Kod Proje Kural Kümelerini Eşitleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod projeleri için kod analizi ayarlarını, en azından iade ilkesi için kural kümesinde belirtilen kuralları içeren bir kural kümesi belirterek takım projesi için iade ilkesiyle eşitlerseniz. Geliştirici liderinize, iade ilkesi için kural kümesinin adı ve konumu hakkında bilgi alabilirsiniz. Proje için kod analizinin doğru kural kümesini kullandığından emin olmak için aşağıdaki seçeneklerden birini kullanabilirsiniz:

- İade ilkesi Microsoft yerleşik kural kümelerinden birini kullanıyorsa, kod projesi için Özellikler iletişim kutusunu açın, kod analizi sayfasını görüntüleyin ve kod projesi ayarları ' nın kod analizi sayfasında ayarlanan kuralı seçin. Microsoft standart kural kümeleri, Visual Studio ile otomatik olarak yüklenir, salt okunurdur ve düzenlenmemelidir. Kural kümeleri düzenlenmediği takdirde, ilke ve yerel kural kümelerindeki kuralların eşleşmesi garanti edilir.

- İade ilkesi özel bir kural kümesi kullanıyorsa, yerel bir kopya oluşturmak için sürüm denetimindeki kural kümesi dosyasında bir get işlemi gerçekleştirin. Ardından, kod projesi için kod analizi ayarlarında bu yerel konumu belirtin. İade ilkesi için kural kümesi güncel ise kuralların eşleşmesi garanti edilir.

     Sürüm denetim konumunu, kod projeniz olarak takım projesi köküyle aynı ilişkide olan yerel bir klasörle eşleştirdiğinizde, kuralın konumu göreli bir yol kullanılarak ayarlanır. Göreli yol, kod analizi için kod projesi ayarının diğer bilgisayarlara taşınabilmesini sağlar.

- Bir kod projesi için iade ilkesi için kural kümesinin bir kopyasını özelleştirin. Yeni kural kümesinin, iade ilkesindeki tüm kuralları ve dahil etmek istediğiniz diğer kuralları içerdiğinden emin olun. Kural kümesi 'nin, iade ilkesi için kural kümesindeki tüm kuralları içerdiğinden emin olmanız gerekir.

### <a name="to-specify-a-microsoft-standard-rule-set"></a>Bir Microsoft standart kural kümesi belirtmek için

1. **Çözüm Gezgini**, kod projesine sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. **Kod Analizi**' ne tıklayın.

3. **Bu kural kümesini Çalıştır** listesinde, iade ilkesi kural kümesine tıklayın.

### <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Özel bir iade ilkesi kural kümesi belirtmek için

1. Gerekirse, iade ilkesini belirten kural kümesi dosyasında bir get işlemi gerçekleştirin.

2. **Çözüm Gezgini**, kod projesine sağ tıklayın ve ardından **Özellikler**' e tıklayın.

3. **Kod Analizi**' ne tıklayın.

4. **Bu kural kümesini Çalıştır** listesinde, öğesine tıklayın **\<Browse...>** .

5. **Aç** iletişim kutusunda, iade ilkesi kural kümesi dosyasını belirtin.

### <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Bir kod projesi için özel bir kural kümesi oluşturmak için

1. Bu konunun önceki kısımlarında yer alan yordamlardan birini izleyerek, proje ayarları iletişim kutusunun Kod Analizi sayfasında takım projesinin iade ilkesini seçin.

2. **Aç**’a tıklayın.

3. Kural kümesi düzenleyicisini kullanarak kural ekleyin veya kaldırın.

     Daha fazla bilgi için bkz. [özel kural kümeleri oluşturma](../code-quality/creating-custom-code-analysis-rule-sets.md).

4. Değiştirilen kural kümesini yerel bilgisayardaki bir. RuleSet dosyasına veya bir UNC yoluna kaydedin.

5. Kod projesi için Özellikler iletişim kutusunu açın ve **Kod Analizi** sayfasını görüntüleyin.

6. **Bu kural kümesini Çalıştır** listesinde, öğesine tıklayın **\<Browse...>** .

7. **Aç** iletişim kutusunda, kural kümesi dosyasını belirtin.
