---
title: Kod analizini yapılandırma
ms.date: 04/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f1bfa8c6e5260fb4afd20b882e2bdfc718647f4b
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448976"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Nasıl yapılır: yönetilen kod için eski Analizi yapılandırma

Visual Studio 'da, yönetilen bir kod projesine uygulamak üzere kod analizi [kural kümeleri](../code-quality/rule-set-reference.md) listesinden seçim yapabilirsiniz. Varsayılan olarak, **En düşük önerilen kurallar** kural kümesi seçilidir, ancak isterseniz farklı bir kural kümesi uygulayabilirsiniz. Kural kümeleri, bir çözümdeki bir veya birden çok projeye uygulanabilir.

> [!NOTE]
> Bu makale, [.net Compiler platform tabanlı kod Çözümleyicileri](use-roslyn-analyzers.md)için değil, eski analizler için geçerlidir.

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>.NET Framework projesi için bir kural kümesi yapılandırma

1. Projenin özellik sayfalarındaki **Kod Analizi** sekmesini açın. Bunu aşağıdaki yöntemlerle yapabilirsiniz:

   - **Çözüm Gezgini**, projeyi seçin. Menü çubuğunda **çözümle** >  **\<Projectname > Için** **Kod analizini Yapılandır** >  ' ü seçin.

   - **Çözüm Gezgini** ' de projeye sağ tıklayın ve **Özellikler**' i seçin ve ardından **Kod Analizi** sekmesini seçin.

2. **Yapılandırma** ve **Platform** listelerinde, derleme yapılandırması ve hedef platform ' u seçin.

::: moniker range="vs-2017"

3. Projenin seçili yapılandırma kullanılarak oluşturulduğu her seferinde Kod analizini çalıştırmak için **derlemede Kod analizini etkinleştir**' i seçin. Kod analizini **çözümle** > **kod analizini Çalıştır** >  **' ü \<projectname > üzerinde**kod analizi Çalıştır ' a el ile de çalıştırabilirsiniz.

::: moniker-end

::: moniker range=">=vs-2019"

3. Projenin seçili yapılandırma kullanılarak oluşturulduğu her seferinde Kod analizini çalıştırmak için, **ikili çözümleyiciler** bölümündeki **derlemede Çalıştır** ' ı seçin. Kod analizini **çözümle** > **kod analizini Çalıştır** >  **' ü \<projectname > üzerinde**kod analizi Çalıştır ' a el ile de çalıştırabilirsiniz.

::: moniker-end

4. Oluşturulan koddan gelen uyarıları görüntülemek için, **oluşturulan koddan sonuçları bastır** onay kutusunun işaretini kaldırın.

    > [!NOTE]
    > Bu seçenek, hatalar ve uyarılar formlarda ve şablonlarda görüntülendiğinde, kod analizi hatalarını ve üretilen koddan gelen uyarıları göstermez. Bir form veya şablon için kaynak kodu görüntüleyebilir ve bakımını yapabilir ve üzerine yazılmaz.

::: moniker range="vs-2017"

5. **Bu kural kümesini Çalıştır** listesinde aşağıdakilerden birini yapın:

::: moniker-end

::: moniker range=">=vs-2019"

5. **Etkin kurallar** listesinde aşağıdakilerden birini yapın:

::: moniker-end

    - Kullanmak istediğiniz kural kümesini seçin.

    - Listede olmayan var olan bir özel kural kümesini bulmak için **\<Taraya >** seçin.

    - Özel bir [kural kümesi](../code-quality/how-to-create-a-custom-rule-set.md)tanımlayın.

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Bir çözümde birden çok proje için kural kümesi belirtme

Varsayılan olarak, bir çözümün tüm yönetilen projelerine, *Microsoft 'un önerilen en düşük kural* kodu çözümleme kuralı kümesi atanır. Çözümün projelerine atanmış kural kümelerini çözüm için **Özellikler** iletişim kutusunda değiştirebilirsiniz.

1. Visual Studio 'da çözümü açın.

2. **Çözümle** menüsünde, **çözüm Için kod analizini Yapılandır**' ı seçin.

3. Gerekirse, **ortak özellikler**' i genişletin ve ardından **Kod Analizi ayarları**' nı seçin.

4. Bir veya daha fazla proje için bir kural kümesi belirtebilirsiniz:

    - Tek bir proje için bir kural kümesi belirtmek üzere proje adını seçin.

    - Birden çok proje için bir kural kümesi belirtmek için **CTRL** tuşunu basılı tutun ve proje adlarını seçin.

    - Çözümdeki tüm projeleri belirtmek için **SHIFT** tuşunu basılı tutun ve proje listesine tıklayın.

5. Bir projenin **kural kümesi** alanını seçin ve ardından uygulamak istediğiniz kural kümesinin adını seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod çözümleme kural kümesi başvurusu](../code-quality/rule-set-reference.md)
