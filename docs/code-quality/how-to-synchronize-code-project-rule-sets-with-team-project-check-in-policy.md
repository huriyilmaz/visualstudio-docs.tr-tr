---
title: Proje kural kümelerini iade ilkesiyle eşitleme
ms.date: 11/04/2016
description: Visual Studio proje Azure DevOps ilkesiyle eşitlemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 20c4d0c6fc5583686648507be2a36c5183ca70c6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631922"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-an-azure-devops-project-check-in-policy"></a>Nasıl edilir: Kod Project Kural Kümelerini Azure DevOps Project İlkeyle Eşitleme

En azından iade ilkesi için kural kümesinde belirtilen kuralları içeren bir kural kümesi belirterek kod projeleri için kod analizi ayarlarını Azure DevOps projesinin iade ilkesiyle eşitlersiniz. Geliştirici müşteri adayınız, iade ilkesi için kural kümesi adını ve konumunu size bildirebilirsiniz. Proje için kod analizinin doğru kural kümesi kullandığına emin olmak için aşağıdaki seçeneklerden birini kullanabilirsiniz:

- Iade ilkesi Microsoft'un yerleşik kural kümelerinden birini kullanıyorsa, kod projesinin özellikler iletişim kutusunu açın, Code Analysis sayfasını açın ve kural kümesi seçin. Microsoft standart kural kümeleri, salt okunur Visual Studio otomatik olarak yüklenir ve düzenlenemez. Kural kümeleri düzenlenemezse, ilke ve yerel kural kümelerinde yer alan kuralların eşleşmesi garantidir.

- Iade ilkesi özel bir kural kümesi kullanıyorsa, yerel bir kopya oluşturmak için sürüm denetiminde kural kümesi dosyasında bir get işlemi gerçekleştirin. Ardından kod projesinin kod analizi ayarlarında bu yerel konumu belirtin. Giriş ilkesi için kural kümesi güncelse kuralların eşleşmesi garantidir.

     Sürüm denetimi konumunu kod projeniz ile Azure DevOps proje köküyle aynı ilişkide olan yerel bir klasöre eşlersanız, kuralın konumu göreli bir yol kullanılarak ayarlanır. Göreli yol, kod analizi için kod projesi ayarının diğer bilgisayarlara taşınamalarını sağlar.

- Kod projesi için iade ilkesi için kural kümesi kopyasını özelleştirin. Yeni kural kümesinde iade ilkesinde yer alan tüm kuralların ve dahil etmek istediğiniz diğer kuralların olduğundan emin olun. Kural kümenizin, iade ilkesi için kural kümesinde yer alan tüm kuralları içerir.

## <a name="to-specify-a-microsoft-standard-rule-set"></a>Microsoft standart kural kümesi belirtmek için

1. Bu **Çözüm Gezgini,** kod projesine sağ tıklayın ve ardından Özellikler'e **tıklayın.**

2. Öğesini Code Analysis.

::: moniker range="vs-2017"

3. Bu **kural kümesi çalıştır listesinde,** iade ilkesi kural kümesi seçin.

::: moniker-end

::: moniker range=">=vs-2019"

3. Etkin **kurallar listesinde** iade ilkesi kural kümesi'ne tıklayın.

::: moniker-end

## <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Özel bir iade ilkesi kural kümesi belirtmek için

1. Gerekirse, kural kümesi dosyasında iade ilkesi belirten bir get işlemi gerçekleştirin.

2. Bu **Çözüm Gezgini,** kod projesine sağ tıklayın ve ardından Özellikler'e **tıklayın.**

3. Öğesini Code Analysis.

::: moniker range="vs-2017"

4. Bu kuralı **çalıştır kümesi listesinde'ye** **\<Browse>** tıklayın.

::: moniker-end

::: moniker range=">=vs-2019"

4. Etkin **kurallar listesinde'ye** **\<Browse>** tıklayın.

::: moniker-end

5. Aç **iletişim** kutusunda, iade ilkesi kural kümesi dosyasını belirtin.

## <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Kod projesi için özel bir kural kümesi oluşturmak için

Özel kural kümesi oluşturma hakkında bilgi için [bkz. Kural kümesi özelleştirme.](how-to-create-a-custom-rule-set.md)
