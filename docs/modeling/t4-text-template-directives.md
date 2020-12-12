---
title: T4 Metin Şablonu Yönergeleri
description: T4 test şablonu yönergeleri ve bunların metin şablonu dönüştürme altyapısına nasıl yönergeler sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, import directive
- text templates, include directive
- text templates, assembly directive
- text templates, output directive
- text templates, directives
- text templates, template directive
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ddad0010413ebe8e0a53096bb4d90b52050d26a
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363607"
---
# <a name="t4-text-template-directives"></a>T4 Metin Şablonu Yönergeleri

Yönergeler metin şablonu dönüştürme motoru için yönergeler sağlar.

Yönergelerin sözdizimi aşağıdaki gibidir:

```
<#@ DirectiveName [AttributeName = "AttributeValue"] ... #>
```

Tüm öznitelik değerleri çift tırnak işaretleri arasına alınmalıdır. Değerin kendisi tırnak işaretleri içeriyorsa, bunlardan \ karakteriyle kaçılmalıdır.

Yönergeler genellikle şablon dosyasında ya da eklenen dosyadaki ilk öğelerdir. Bunları bir kod bloğunun içine `<#...#>` veya bir sınıf özelliği bloğundan sonra yerleştirmemelisiniz `<#+...#>` .

[T4 Şablon Yönergesi](../modeling/t4-template-directive.md)

```
<#@ template [language="VB"] [hostspecific="true|TrueFromBase"] [debug="true"] [inherits="templateBaseClass"] [culture="code"] [compilerOptions="options"] [visibility="internal"] [linePragmas="false"] #>
```

[T4 Parametre Yönergesi](../modeling/t4-parameter-directive.md)

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

[T4 Çıkış Yönergesi](../modeling/t4-output-directive.md)

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

[T4 Derleme Yönergesi](../modeling/t4-assembly-directive.md)

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

[T4 İçe Aktarma Yönergesi](../modeling/t4-import-directive.md)

```
<#@ import namespace="namespace" #>
```

[T4 Include Yönergesi](../modeling/t4-include-directive.md)

```
<#@ include file="filePath" #>
```

[T4 CleanUpBehavior yönergesi](../modeling/t4-cleanupbehavior-directive.md)

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

Ayrıca, kendi yönergelerinizi oluşturabilirsiniz. Daha fazla bilgi için bkz. [özel T4 metin şablonu yönerge Işlemcileri oluşturma](../modeling/creating-custom-t4-text-template-directive-processors.md). Görselleştirme ve Modelleme SDK'sını etki alanına özgü dil (DSL) oluşturmak için kullanıyorsanız, bir yönerge işlemcisi, DSL'nin bir parçası olarak oluşturulur.
