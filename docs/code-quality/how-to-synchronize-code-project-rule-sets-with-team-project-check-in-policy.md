---
title: İade ilkesiyle proje kural kümelerini eşitleme
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe6e9e49998c3e98335cd7e873d53531c8bfa99a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649378"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-an-azure-devops-project-check-in-policy"></a>Nasıl yapılır: Azure DevOps projesi Iade Ilkesiyle kod proje kural kümelerini senkronize etme

Kod projeleri için kod analizi ayarlarını, en azından iade ilkesi için kural kümesinde belirtilen kuralları içeren bir kural kümesi belirterek Azure DevOps projesi için iade etme ilkesiyle eşitlerseniz. Geliştirici liderinize, iade ilkesi için kural kümesinin adı ve konumu hakkında bilgi alabilirsiniz. Proje için kod analizinin doğru kural kümesini kullandığından emin olmak için aşağıdaki seçeneklerden birini kullanabilirsiniz:

- İade ilkesi Microsoft yerleşik kural kümelerinden birini kullanıyorsa, kod projesi için Özellikler iletişim kutusunu açın, kod analizi sayfasını görüntüleyin ve kural kümesini seçin. Microsoft standart kural kümeleri, Visual Studio ile otomatik olarak yüklenir, salt okunurdur ve düzenlenmemelidir. Kural kümeleri düzenlenmediği takdirde, ilke ve yerel kural kümelerindeki kuralların eşleşmesi garanti edilir.

- İade ilkesi özel bir kural kümesi kullanıyorsa, yerel bir kopya oluşturmak için sürüm denetimindeki kural kümesi dosyasında bir get işlemi gerçekleştirin. Ardından, kod projesi için kod analizi ayarlarında bu yerel konumu belirtin. İade ilkesi için kural kümesi güncel ise kuralların eşleşmesi garanti edilir.

     Sürüm denetim konumunu, kod projeniz olarak Azure DevOps proje köküyle aynı ilişkide olan bir yerel klasörle eşleştirdiğinizde, kuralın konumu göreli bir yol kullanılarak ayarlanır. Göreli yol, kod analizi için kod projesi ayarının diğer bilgisayarlara taşınabilmesini sağlar.

- Bir kod projesi için iade ilkesi için kural kümesinin bir kopyasını özelleştirin. Yeni kural kümesinin, iade ilkesindeki tüm kuralları ve dahil etmek istediğiniz diğer kuralları içerdiğinden emin olun. Kural kümesi 'nin, iade ilkesi için kural kümesindeki tüm kuralları içerdiğinden emin olmanız gerekir.

## <a name="to-specify-a-microsoft-standard-rule-set"></a>Bir Microsoft standart kural kümesi belirtmek için

1. **Çözüm Gezgini**, kod projesine sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. **Kod Analizi**' ne tıklayın.

::: moniker range="vs-2017"

3. **Bu kural kümesini Çalıştır** listesinde, iade ilkesi kural kümesini seçin.

::: moniker-end

::: moniker range=">=vs-2019"

3. **Etkin kurallar** listesinde, iade ilkesi kural kümesini seçin.

::: moniker-end

## <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Özel bir iade ilkesi kural kümesi belirtmek için

1. Gerekirse, iade ilkesini belirten kural kümesi dosyasında bir get işlemi gerçekleştirin.

2. **Çözüm Gezgini**, kod projesine sağ tıklayın ve ardından **Özellikler**' e tıklayın.

3. **Kod Analizi**' ne tıklayın.

::: moniker range="vs-2017"

4. **Bu kural kümesini Çalıştır** listesinde **\<zat >** ' a tıklayın.

::: moniker-end

::: moniker range=">=vs-2019"

4. **Etkin kurallar** listesinde **\<Browse >** ' ne tıklayın.

::: moniker-end

5. **Aç** iletişim kutusunda, iade ilkesi kural kümesi dosyasını belirtin.

## <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Bir kod projesi için özel bir kural kümesi oluşturmak için

Özel bir kural kümesi oluşturma hakkında daha fazla bilgi için bkz. [bir kural kümesini özelleştirme](how-to-create-a-custom-rule-set.md).
