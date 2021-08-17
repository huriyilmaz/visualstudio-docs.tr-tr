---
title: Code Analysis Yapılandır
ms.date: 04/04/2018
description: eski kod analizinin kullandığı Visual Studio kural kümesini nasıl yapılandıracağınızı öğrenin. Bir çözümdeki bir veya birden çok projeye nasıl kural kümesi uygulanacağını öğrenin.
ms.custom: SEO-VS-2020
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
- vs.codeanalysis.propertypages.asp
dev_langs:
- CSharp
- VB
- FSharp
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 645441b8961ca84534bd9f4a503189ceb2cb5ab3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122122156"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Nasıl yapılır: yönetilen kod için eski Analizi yapılandırma

Visual Studio, yönetilen bir kod projesine uygulamak için kod analizi [kural kümeleri](../code-quality/rule-set-reference.md) listesinden seçim yapabilirsiniz. Varsayılan olarak, **En düşük önerilen kurallar** kural kümesi seçilidir, ancak isterseniz farklı bir kural kümesi uygulayabilirsiniz. Kural kümeleri, bir çözümdeki bir veya birden çok projeye uygulanabilir.

> [!NOTE]
> bu makale, [.NET Compiler Platform tabanlı kod çözümleyicileri](use-roslyn-analyzers.md)için değil, eski analizler için geçerlidir.

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>.NET Framework projesi için bir kural kümesi yapılandırma

1. projenin özellik sayfalarındaki **Code Analysis** sekmesini açın. Bunu aşağıdaki yöntemlerle yapabilirsiniz:

   - **Çözüm Gezgini**, projeyi seçin. menü çubuğunda **analiz**  >  **Code Analysis**  >  **\<projectname>** yapılandır ' ı seçin.

   - **Çözüm Gezgini** ' de projeye sağ tıklayın ve **özellikler**' i seçin ve ardından **Code Analysis** sekmesini seçin.

2. **Yapılandırma** ve **Platform** listelerinde, derleme yapılandırması ve hedef platform ' u seçin.

::: moniker range="vs-2017"

3. projenin seçili yapılandırma kullanılarak oluşturulduğu her seferinde kod analizini çalıştırmak için, **derlemede Code Analysis etkinleştir**' i seçin. kod analizini ayrıca,   >  **çalıştır Code Analysis** çalıştır '  >  **\<projectname>** i seçerek el ile de çalıştırabilirsiniz Code Analysis.

::: moniker-end

::: moniker range=">=vs-2019"

3. Projenin seçili yapılandırma kullanılarak oluşturulduğu her seferinde Kod analizini çalıştırmak için, **ikili çözümleyiciler** bölümündeki **derlemede Çalıştır** ' ı seçin. eski kod analizini el ile de çalıştırabilirsiniz, daha fazla ayrıntı için bkz. [nasıl yapılır: eski Code Analysis yönetilen kod için el ile çalıştırma](how-to-run-legacy-code-analysis-manually-for-managed-code.md) .

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

   - **\<Browse>** Listede olmayan mevcut bir özel kural kümesini bulmak için seçin.

   - Özel bir [kural kümesi](../code-quality/how-to-create-a-custom-rule-set.md)tanımlayın.

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Bir çözümde birden çok proje için kural kümesi belirtme

Varsayılan olarak, bir çözümün tüm yönetilen projelerine, *Microsoft 'un önerilen en düşük kural* kodu çözümleme kuralı kümesi atanır. Çözümün projelerine atanmış kural kümelerini çözüm için **Özellikler** iletişim kutusunda değiştirebilirsiniz.

1. Çözümü Visual Studio açın.

2. **çözümle** menüsünde, **çözüm için Code Analysis yapılandır**' ı seçin.

3. gerekirse, **ortak özellikler**' i genişletin ve ardından **Code Analysis Ayarlar**' ni seçin.

4. Bir veya daha fazla proje için bir kural kümesi belirtebilirsiniz:

    - Tek bir proje için bir kural kümesi belirtmek üzere proje adını seçin.

    - Birden çok proje için bir kural kümesi belirtmek üzere **CTRL** ve proje adlarını seçin.

    - Çözümdeki tüm projeleri belirtmek için, **Shift** ve proje listesi ' ni seçin.

5. Bir projenin **kural kümesi** alanını seçin ve ardından uygulamak istediğiniz kural kümesinin adını seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod çözümleme kural kümesi başvurusu](../code-quality/rule-set-reference.md)
