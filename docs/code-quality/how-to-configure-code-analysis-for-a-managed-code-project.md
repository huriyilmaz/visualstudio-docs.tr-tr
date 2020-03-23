---
title: Kod Analizini Yapılandırma
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
ms.openlocfilehash: 98db7cda02495d207d6e9387341173ea2efe22ca
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431358"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Nasıl yapilir: Yönetilen kod için eski çözümlemeyi yapılandırma

Visual Studio'da, yönetilen kod projesine uygulanacak kod çözümleme [kural kümeleri](../code-quality/rule-set-reference.md) listesinden seçim yapabilirsiniz. Varsayılan olarak, **Microsoft Minimum Önerilen Kurallar** kuralı kümesi seçilir, ancak istenirse farklı bir kural kümesi uygulayabilirsiniz. Kural kümeleri bir çözümde bir veya birden çok projeye uygulanabilir.

> [!NOTE]
> Bu makale, [.NET Derleyici Platformu tabanlı kod çözümleyicileri](use-roslyn-analyzers.md)için değil, eski çözümleme için geçerlidir.

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>.NET Framework projesi için ayarlanan kuralı yapılandırma

1. Projenin özellik sayfalarındaki **Kod Analizi** sekmesini açın. Bunu aşağıdaki yollardan biri olarak yapabilirsiniz:

   - **Çözüm Gezgini'nde**projeyi seçin. Menü çubuğunda,**proje adı>\<için ****Yapıyı Kod Analizini** >  **Analiz** > Et'i seçin.

   - **Solution Explorer'da** projeyi sağ tıklatın ve **Özellikler'i**seçin ve ardından **Kod Çözümlemesi** sekmesini seçin.

2. **Yapılandırma** ve **Platform** listelerinde yapı yapılandırmasını ve hedef platform'u seçin.

::: moniker range="vs-2017"

3. Proje seçili yapılandırmayı kullanarak her oluşturultuca kod çözümlemesi çalıştırmak için **Yapı'da Kod Çözümlemesini Etkinleştir'i**seçin. **Analyze** > Ayrıca**proje adı>analiz kodu analizini seçerek kod çözümlemesi el ile çalıştırabilirsiniz. \< ****Run Code Analysis** > 

::: moniker-end

::: moniker range=">=vs-2019"

3. Proje seçili yapılandırmakullanılarak her oluşturultuca kod çözümlemesi çalıştırmak için **İkili çözümleyiciler** bölümünde **yapıda Çalıştır'ı** seçin. Ayrıca eski kod çözümlemeyi el ile çalıştırabilirsiniz, [bkz.](how-to-run-legacy-code-analysis-manually-for-managed-code.md)

::: moniker-end

4. Oluşturulan koddaki uyarıları görüntülemek **için, oluşturulan kod onay kutusundan Sonuçları Bastır'ı** temizleyin.

    > [!NOTE]
    > Bu seçenek, formlarda ve şablonlarda hatalar ve uyarılar göründüğünde oluşturulan koddan kaynaklanan kod çözümleme hatalarını ve uyarılarını bastırmaz. Bir form veya şablon için kaynak kodu hem görüntüleyebilir hem de koruyabilirsiniz ve bu kod üzerine yazılmaz.

::: moniker range="vs-2017"

5. Run **bu kural kümesi** listesinde aşağıdakilerden birini yapın:

::: moniker-end

::: moniker range=">=vs-2019"

5. Etkin **kurallar** listesinde aşağıdakilerden birini yapın:

::: moniker-end

   - Kullanmak istediğiniz kural kümesini seçin.

   - Listede olmayan varolan bir özel kural kümesini bulmak için ** \<gözat>'ı** seçin.

   - Özel bir [kural kümesi tanımlayın.](../code-quality/how-to-create-a-custom-rule-set.md)

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Çözümde birden çok proje için kural kümelerini belirtin

Varsayılan olarak, bir çözümün yönetilen tüm projelerine *Microsoft Minimum Önerilen Kurallar* kod çözümleme kuralı kümesi atanır. Çözüm için **Özellikler** iletişim kutusunda bir çözümün projelerine atanan kural kümelerini değiştirebilirsiniz.

1. Çözümü Visual Studio'da açın.

2. **Çözümle** menüsünde Çözüm **için Kod Çözümlemesi'ni yapılandırır'ı**seçin.

3. Gerekirse, **Ortak Özellikleri**genişletin ve ardından **Kod Çözümleme Ayarlarını**seçin.

4. Bir veya daha fazla proje için bir kural kümesi belirtebilirsiniz:

    - Tek bir proje için kural kümesi belirtmek için proje adını seçin.

    - Birden çok proje için ayarlı bir kural belirtmek için **Ctrl'yi** basılı tutun ve proje adlarını seçin.

    - Çözümdeki tüm projeleri belirtmek için **Shift'i** basılı tutun ve proje listesinde tıklatın.

5. Projenin **Kural Kümesi** alanını seçin ve ardından uygulamak istediğiniz kural kümesinin adını seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod çözümleme kural kümesi başvurusu](../code-quality/rule-set-reference.md)
