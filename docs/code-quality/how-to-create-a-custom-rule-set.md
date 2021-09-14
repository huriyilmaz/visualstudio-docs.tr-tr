---
title: Özel kod analizi kural kümesi oluşturma
ms.date: 11/02/2018
description: Kod analizi kural kümelerini nasıl özelleştirebileceğinizi Visual Studio. Sıfırdan veya mevcut kümelerden yeni kümeler oluşturma hakkında daha fazla veri alın. Kural önceliklerini anlama.
ms.custom: SEO-VS-2020
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- rule sets
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 181f94ccc9b83053673e49746d757708afdbf966
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631982"
---
# <a name="customize-a-rule-set"></a>Kural kümesi özelleştirme

Kod analizi için belirli proje ihtiyaçlarını karşılamak üzere özel bir kural kümesi oluşturabilirsiniz.

## <a name="create-a-custom-rule-set-from-an-existing-rule-set"></a>Mevcut bir kural kümesinden özel kural kümesi oluşturma

Özel bir kural kümesi oluşturmak için, kural kümesi düzenleyicisinde yerleşik bir kural **kümesi açabilirsiniz.** Buradan belirli kurallar ekleyebilir veya kaldırabilir ve örneğin bir kural ihlal edildiklerinden oluşan eylemi değiştirebilirsiniz. Örneğin, bir uyarı &mdash; veya hata göster.

1. Bu **Çözüm Gezgini,** projeye sağ tıklayın ve ardından Özellikler'i **seçin.**

2. Özellikler **sayfalarında,** Code Analysis **seçin.**

::: moniker range="vs-2017"

3. Bu **kuralı çalıştır kümesi** açılan listesinde, aşağıdakilerden birini yapın:

::: moniker-end

::: moniker range=">=vs-2019"

3. Etkin **kurallar açılan** listesinde, aşağıdakilerden birini yapın:

::: moniker-end

   - Özelleştirmek istediğiniz kural kümesi seçin.

     \- veya -

   - Listede **\<Browse>** yer alan mevcut bir kural kümesi belirtmek için seçin.

4. Kuralları **kural** kümesi düzenleyicisinde görüntülemek için Aç'ı seçin.

> [!NOTE]
> Bir .NET Core veya .NET Standard projeniz varsa, proje özelliklerinde **Code Analysis** sekmesi aynı seçenekleri desteklemey olduğundan işlem biraz farklıdır. Önceden tanımlanmış bir [kural kümesi kopyalayıp projenize kopyalamak ve](/dotnet/fundamentals/code-analysis/code-quality-rule-options)bunu etkin kural kümesi olarak ayarlamak için adımları izleyin. Bir kural kümesi üzerine kopya kullandıktan [](working-in-the-code-analysis-rule-set-editor.md) sonra, bunu Visual Studio kural kümesi düzenleyicisinde **Çözüm Gezgini.**

## <a name="create-a-new-rule-set"></a>Yeni kural kümesi oluşturma

Yeni Dosya iletişim kutusundan yeni bir kural kümesi **dosyası oluşturabilirsiniz:**

1. Dosya **Yeni**  >  **Dosya'yi**  >  **seçin** veya **Ctrl** N + **tuşlarına basın.**

2. Yeni **Dosya iletişim kutusunda,** sol tarafta **Genel kategorisini** ve ardından Kural Kümesi'Code Analysis **seçin.**

3. **Aç**’ı seçin.

   Yeni *.ruleset dosyası* kural kümesi düzenleyicisinde açılır.

## <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>Birden çok kural kümesinden özel kural kümesi oluşturma

> [!NOTE]
> Aşağıdaki yordam. .NET Core veya .NET Standard projeleri için geçerli değildir. Bu, Code Analysis **sekmesinde** aynı özellikleri desteklemez.

1. Bu **Çözüm Gezgini,** projeye sağ tıklayın ve ardından Özellikler'i **seçin.**

2. Özellikler **sayfalarında,** Code Analysis **seçin.**

::: moniker range="vs-2017"

3. Bu **\<Choose multiple rule sets>** kural kümesi **çalıştır'ı seçin.**

::: moniker-end

::: moniker range=">=vs-2019"

3. Etkin **\<Choose multiple rule sets>** **kurallar'dan öğesini seçin.**

::: moniker-end

4. Kural **Kümesi Ekle veya Kaldır iletişim** kutusunda, yeni kural kümenize eklemek istediğiniz kural kümelerini seçin.

   ![Kural kümesi ekle veya kaldır iletişim kutusu](media/add-remove-rule-sets.png)

5. Farklı **Kaydet'i** seçin, *.ruleset* dosyası için bir ad girin ve kaydet'i **seçin.**

   Yeni kural kümesi Bu kural kümesi çalıştır **listesinde** seçilidir.

6. Kural **kümesi** düzenleyicisinde yeni kural kümesi açmak için Aç'ı seçin.

## <a name="rule-precedence"></a>Kural önceliği

- Aynı kural, farklı ayrımlara sahip bir kural kümesinde iki veya daha fazla kez listelenmişse, derleyici bir hata üretir. Örnek:

   ```xml
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" />
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

- Aynı kural aynı önem derecesine sahip bir kural  kümesinde iki veya daha fazla kez listelenmişse, Hata Listesinde aşağıdaki **uyarıyı görebilir:**

   **CA0063: 'your].ruleset' veya bağımlı kural kümesi dosyalarından biri olan kural \[ kümesi dosyası yüklenemedi. Dosya kural kümesi şemasına uymaz.**

- Kural kümesi, Ekle etiketi kullanılarak bir  alt kural kümesi içerirse ve alt ve üst kural kümeleri her ikisi de aynı kuralı ancak farklı önem dereceleriyle listelese, üst kural kümesinde önem derecesi önceliklidir. Örnek:

   ```xml
   <!-- Parent rule set -->
   <?xml version="1.0" encoding="utf-8"?>
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Include Path="classlibrary_child.ruleset" Action="Default" />
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" /> <!-- Overrides CA1021 severity from child rule set -->
     </Rules>
   </RuleSet>

   <!-- Child rule set -->
   <?xml version="1.0" encoding="utf-8"?>
   <RuleSet Name="Rules from child" Description="Code analysis rules from child." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

## <a name="name-and-description"></a>Ad ve açıklama

Düzenleyicide açık olan bir kural kümesi görünen adını değiştirmek için menü çubuğunda Özellikler **Penceresini** Görüntüle'yi  >   seçerek Özellikler penceresini açın. Ad kutusuna görünen **adı** girin. Kural kümesi için bir açıklama da girsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Artık bir kural kümesine sahip olduğunuza göre, sonraki adım kuralları ekleyerek veya kaldırarak ya da kural ihlallerinin önem derecesini değiştirerek kuralları özelleştirmektir.

> [!div class="nextstepaction"]
> [Kural kümesi düzenleyicisinde kuralları değiştirme](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Yönetilen Kod Projesi İçin Kod Çözümlemesini Yapılandırma](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [Kod çözümleme kural kümesi başvurusu](../code-quality/rule-set-reference.md)