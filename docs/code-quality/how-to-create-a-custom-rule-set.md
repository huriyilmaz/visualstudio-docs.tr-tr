---
title: Özel kod analizi kural kümesi oluşturma
ms.date: 11/02/2018
description: Visual Studio 'de kod analizi kural kümelerini özelleştirmeyi öğrenin. Bkz. sıfırdan veya mevcut kümelerden yeni kümeler oluşturma. Kural önceliğini anlayın.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122139619"
---
# <a name="customize-a-rule-set"></a>Bir kural kümesini özelleştirme

Kod analizi için belirli proje ihtiyaçlarını karşılamak üzere özel bir kural kümesi oluşturabilirsiniz.

## <a name="create-a-custom-rule-set-from-an-existing-rule-set"></a>Var olan bir kural kümesinden özel bir kural kümesi oluşturma

Özel bir kural kümesi oluşturmak için, **kural kümesi düzenleyicisinde** yerleşik bir kural kümesi açabilirsiniz. Buradan, belirli kuralları ekleyebilir veya kaldırabilir ve bir kural ihlal edildiğinde oluşan eylemi değiştirebilirsiniz &mdash; , örneğin bir uyarı veya hata gösterir.

1. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından **Özellikler**' i seçin.

2. **özellikler** sayfalarında **Code Analysis** sekmesini seçin.

::: moniker range="vs-2017"

3. **Bu kural kümesini Çalıştır** açılan listesinde aşağıdakilerden birini yapın:

::: moniker-end

::: moniker range=">=vs-2019"

3. **Etkin kurallar** açılan listesinde aşağıdakilerden birini yapın:

::: moniker-end

   - Özelleştirmek istediğiniz kural kümesini seçin.

     \- veya

   - **\<Browse>** Listede olmayan mevcut bir kural kümesini belirtmek için seçin.

4. Kural kümesi düzenleyicisinde kuralları göstermek için **Aç** ' ı seçin.

> [!NOTE]
> .net Core veya .NET Standard projeniz varsa, proje özelliklerindeki **Code Analysis** sekmesi aynı seçenekleri desteklemediğinden işlem biraz farklıdır. [Önceden tanımlanmış bir kural kümesini projenize kopyalamak ve etkin kural kümesi olarak ayarlamak](/dotnet/fundamentals/code-analysis/code-quality-rule-options)için adımları izleyin. bir kural kümesi üzerinden kopyaladıktan sonra, bunu **Çözüm Gezgini** açarak [Visual Studio kural kümesi düzenleyicisinde düzenleyebilirsiniz](working-in-the-code-analysis-rule-set-editor.md) .

## <a name="create-a-new-rule-set"></a>Yeni bir kural kümesi oluştur

**Yeni dosya** iletişim kutusundan yeni bir kural kümesi dosyası oluşturabilirsiniz:

1. **Dosya**  >  **Yeni**  >  **Dosya**' yı seçin veya **CTRL** + **N** tuşuna basın.

2. **yeni dosya** iletişim kutusunda sol taraftaki **genel** kategorisini seçin ve ardından **Code Analysis kural kümesi**' ni seçin.

3. **Aç**’ı seçin.

   Yeni *. RuleSet* dosyası kural kümesi düzenleyicisinde açılır.

## <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>Birden çok kural kümesinden özel bir kural kümesi oluşturma

> [!NOTE]
> aşağıdaki yordam, .net Core veya .NET Standard projelerine uygulanmaz, bu da **Code Analysis** özellik sekmesindeki özellikleri desteklemez.

1. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından **Özellikler**' i seçin.

2. **özellikler** sayfalarında **Code Analysis** sekmesini seçin.

::: moniker range="vs-2017"

3. **\<Choose multiple rule sets>** **Bu kural kümesini Çalıştır**' ı seçin.

::: moniker-end

::: moniker range=">=vs-2019"

3. **\<Choose multiple rule sets>** **Etkin kurallar** arasından seçim yapın.

::: moniker-end

4. **Kural kümeleri Ekle veya Kaldır** iletişim kutusunda yeni kural kümesine dahil etmek istediğiniz kural kümelerini seçin.

   ![Kural kümeleri Ekle veya Kaldır iletişim kutusu](media/add-remove-rule-sets.png)

5. **Farklı kaydet**' i seçin, *. RuleSet* dosyası için bir ad girin ve ardından **Kaydet**' i seçin.

   Yeni kural kümesi **Bu kural kümesini Çalıştır** listesinde seçilir.

6. Kural kümesi düzenleyicisinde yeni kural kümesini açmak için **Aç** ' ı seçin.

## <a name="rule-precedence"></a>Kural önceliği

- Aynı kural, farklı önem derecelerine sahip bir kural kümesinde iki veya daha fazla kez listeleniyorsa, derleyici bir hata oluşturur. Örnek:

   ```xml
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" />
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

- *Aynı önem derecesine* sahip bir kural kümesinde aynı kural iki veya daha fazla kez listeleniyorsa, **hata listesi** aşağıdaki uyarıyı görebilirsiniz:

   **CA0063: ' \[ sizin]. RuleSet ' kural kümesi dosyası veya bağımlı kural kümesi dosyalarından biri yüklenemedi. Dosya, kural kümesi şemasıyla uyumlu değil.**

- Kural kümesi bir **içerme** etiketi kullanarak ayarlanmış bir alt kural içeriyorsa ve alt ve üst kural her ikisi de aynı kuralı, ancak farklı önem derecelerine sahip olarak ayarlarsa, üst kural kümesindeki önem derecesi önceliklidir. Örnek:

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

Düzenleyicide açık olan bir kural kümesinin görünen adını değiştirmek için,    >  menü çubuğunda **Özellikler penceresini** görüntüle ' yi seçerek Özellikler penceresini açın. **Ad** kutusuna görünen adı girin. Kural kümesi için bir açıklama de girebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Artık bir kural ayarlamış olduğunuza göre, bir sonraki adım kuralları ekleyip kaldırarak veya kural ihlallerinin önem derecesini değiştirerek kuralları özelleştirecek.

> [!div class="nextstepaction"]
> [Kural kümesi düzenleyicisinde kuralları değiştirme](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Yönetilen Kod Projesi İçin Kod Çözümlemesini Yapılandırma](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [Kod çözümleme kural kümesi başvurusu](../code-quality/rule-set-reference.md)