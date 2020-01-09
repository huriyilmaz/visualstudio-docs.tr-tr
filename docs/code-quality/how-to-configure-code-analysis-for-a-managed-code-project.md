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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: fe144e8de67264c9d89f6a240ef815afac9a4655
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587569"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Nasıl yapılır: yönetilen kod için eski Analizi yapılandırma

Visual Studio 'da, yönetilen bir kod projesine uygulamak üzere kod analizi [kural kümeleri](../code-quality/rule-set-reference.md) listesinden seçim yapabilirsiniz. Varsayılan olarak, **Microsoft en az önerilen kurallar** kural kümesi işaretli, ancak isterseniz kümesi farklı bir kural uygulayabilirsiniz. Bir çözümde bir veya birden çok proje için kural kümeleri uygulanabilir.

> [!NOTE]
> Bu makale, [.net Compiler platform tabanlı kod Çözümleyicileri](use-roslyn-analyzers.md)için değil, eski analizler için geçerlidir.

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>.NET Framework projesi için bir kural kümesi yapılandırma

1. Açık **Kod Analizi** projenin özellik sayfalarındaki sekmesinde. Bunu, aşağıdaki yollardan biriyle yapabilirsiniz:

   - İçinde **Çözüm Gezgini**, projeyi seçin. Menü çubuğunda, seçin **Çözümle** > **Kod Analizi yapılandırma** > **için \<projectname >** .

   - Projeye sağ **Çözüm Gezgini** seçip **özellikleri**ve ardından **Kod Analizi** sekmesi.

2. İçinde **yapılandırma** ve **Platform** listeleri, derleme yapılandırması ve hedef platformu seçin.

::: moniker range="vs-2017"

3. Projenin seçili yapılandırma kullanılarak oluşturulduğu her seferinde Kod analizini çalıştırmak için **derlemede Kod analizini etkinleştir**' i seçin. Ayrıca kod analizini el ile seçerek çalıştırabilirsiniz **Çözümle** > **kod çözümlemeyi Çalıştır** > **kod çözümlemeyi Çalıştır \<projectname >** .

::: moniker-end

::: moniker range=">=vs-2019"

3. Projenin seçili yapılandırma kullanılarak oluşturulduğu her seferinde Kod analizini çalıştırmak için, **ikili çözümleyiciler** bölümündeki **derlemede Çalıştır** ' ı seçin. Ayrıca kod analizini el ile seçerek çalıştırabilirsiniz **Çözümle** > **kod çözümlemeyi Çalıştır** > **kod çözümlemeyi Çalıştır \<projectname >** .

::: moniker-end

4. Üretilen koddan gelen uyarıları görüntülemek için temizleyin **üretilen koddan gelen sonuçları Gizle** onay kutusu.

    > [!NOTE]
    > Bu seçenek hataları ve Uyarıları formları ve şablonlar görüntülendiğinde kod çözümleme hataları ve Uyarıları üretilen koddan gelen engellemez. Bir form veya şablon için kaynak kodu görüntüleyebilir ve bakımını yapabilir ve üzerine yazılmaz.

::: moniker range="vs-2017"

5. İçinde **bu kural kümesini Çalıştır** listesinde, aşağıdakilerden birini yapın:

::: moniker-end

::: moniker range=">=vs-2019"

5. **Etkin kurallar** listesinde aşağıdakilerden birini yapın:

::: moniker-end

   - Kullanmak istediğiniz bir kural kümesi seçin.

   - Listede olmayan var olan bir özel kural kümesini bulmak için **\<> gözatıp** ' yi seçin.

   - Tanımlayan bir [özel kural kümesi](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Bir çözümde birden çok proje için kural kümeleri belirtin

Varsayılan olarak, bir çözümün tüm yönetilen projelere atanır *Microsoft en az önerilen kurallar* Kod Analizi kural kümesi. Bir Çözümdeki projeler için atanan kural kümeleri değiştirebilirsiniz **özellikleri** çözümü iletişim kutusu.

1. Visual Studio içinde çözümü açın.

2. Üzerinde **Çözümle** menüsünde **çözüm için Kod Analizi yapılandırma**.

3. Gerekirse genişletin **ortak özellikler**ve ardından **Kod Analizi ayarları**.

4. Bir veya daha fazla proje için bir kural belirtebilirsiniz:

    - Bir kural kümesi için bir projeyi belirtmek için proje adını seçin.

    - Birden çok proje için bir kural belirtmek için basılı **Ctrl** ve proje adları seçin.

    - Çözümdeki tüm projeleri belirtmek için basılı **Shift** ve Proje listesinde tıklayın.

5. Seçin **kural kümesi** bir proje alanı ve ardından uygulamak istediğiniz kuralın adını ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod çözümleme kural kümesi başvurusu](../code-quality/rule-set-reference.md)
