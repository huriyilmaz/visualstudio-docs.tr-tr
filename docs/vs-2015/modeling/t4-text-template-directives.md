---
title: T4 metin şablonu yönergeleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, import directive
- text templates, include directive
- text templates, assembly directive
- text templates, output directive
- text templates, directives
- text templates, template directive
ms.assetid: 6898ee02-ebb2-4635-a4e9-350774c13cf2
caps.latest.revision: 83
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6d77c7a779afcbf7bc7fc3f8fbd863aa368ee7e6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658546"
---
# <a name="t4-text-template-directives"></a>T4 Metin Şablonu Yönergeleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yönergeler metin şablonu dönüştürme motoru için yönergeler sağlar.

 Yönergelerin sözdizimi aşağıdaki gibidir:

```
<#@ DirectiveName [AttributeName = "AttributeValue"] ... #>
```

 Tüm öznitelik değerleri çift tırnak işaretleri arasına alınmalıdır. Değerin kendisi tırnak işaretleri içeriyorsa, bunlardan \ karakteriyle kaçılmalıdır.

 Yönergeler genellikle şablon dosyasında ya da eklenen dosyadaki ilk öğelerdir. Bir sınıf özelliği bloğunun `<#+...#>` `<#...#>` bir kod bloğunun içine yerleştirmemelisiniz.

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
