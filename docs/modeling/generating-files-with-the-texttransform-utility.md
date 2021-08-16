---
title: TextTransform Yardımcı Programı ile Dosya Oluşturma
description: TextTransform yardımcı programını, metin şablonunu dönüştürmek için kullanabileceğiniz bir komut satırı aracı olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 07/26/2019
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: d230256d988c16d86e01fc04e363d40473b1ac1a35e1c9bdc45faa3de3c43b25
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121271335"
---
# <a name="generate-files-with-the-texttransform-utility"></a>TextTransform yardımcı programıyla dosya oluşturma

TextTransform.exe, metin şablonunu dönüştürmek için kullanabileceğiniz bir komut satırı aracıdır. Bir metin TextTransform.exe, bir metin şablonu dosyasının adını bağımsız değişken olarak belirtirsiniz. TextTransform.exe dönüştürme altyapısını çağırarak metin şablonunu işlemesini sağlar. TextTransform.exe genellikle betiklerden çağrılır. Ancak genellikle gerekli değildir çünkü metin dönüştürme işlemini hem Visual Studio işlemiyle gerçekleştirebilirsiniz.

> [!NOTE]
> Derleme işleminin bir parçası olarak metin dönüşümü gerçekleştirmek için metin dönüştürme görevini MSBuild düşünün. Daha fazla bilgi için [bkz. Derleme İşlemsinde Kod Oluşturma.](../modeling/code-generation-in-a-build-process.md) Uygulamanın yük Visual Studio makinede, metin şablonlarını dönüştüren bir uygulama veya Visual Studio Uzantısı da yazabilirsiniz. Daha fazla bilgi için [bkz. Özel Ana Bilgisayar Kullanarak Metin Şablonlarını İşleme.](../modeling/processing-text-templates-by-using-a-custom-host.md)

TextTransform.exe aşağıdaki dizinde bulunur:

::: moniker range=">=vs-2019"

**\Program Files (x86)\Microsoft Visual Studio\2019\Professional\Common7\IDE**

Professional sürümü için veya

**\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE**

Enterprise sürümü için.

::: moniker-end

::: moniker range="vs-2017"

**\Program Files (x86)\Microsoft Visual Studio\2017\Professional\Common7\IDE**

Professional sürümü için veya

**\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

Enterprise sürümü için.

Önceki Visual Studio dosya aşağıdaki konumda bulunur:

**\Program Files (x86)\Common Files\Microsoft Shared\TextTemplating \{ version}**

burada {version} hangi önceki sürümün yüklü olduğunu bağlıdır.

::: moniker-end

## <a name="syntax"></a>Sözdizimi

```
TextTransform [<options>] <templateName>
```

### <a name="parameters"></a>Parametreler

|**Bağımsız değişken**|**Açıklama**|
|-|-|
|`templateName`|Dönüştürmek istediğiniz şablon dosyasının adını tanımlar.|

|**Seçenek**|**Açıklama**|
|-|-|
|**-out**\<filename>|Dönüşümün çıkışını yazıldığı dosya.|
|**-r**\<assembly>|Metin şablonunu derlemek ve çalıştırmak için kullanılan derleme.|
|**-u**\<namespace>|Şablonu derlemek için kullanılan bir ad alanı.|
|**-I**\<includedirectory>|Belirtilen metin şablonuna dahil edilen metin şablonlarını içeren bir dizin.|
|**-P**\<referencepath>|Metin şablonu içinde belirtilen derlemeleri aramak veya -r seçeneğini kullanmak için **bir dizin.**<br /><br /> Örneğin, Visual Studio API'si için kullanılan derlemeleri dahil etmek için kullanın<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName> ! \<className> !\<assemblyName&#124;codeBase>|Metin şablonu içindeki özel yönergeleri işlemede kullanılan yönerge işlemcisinin adı, tam tür adı ve derlemesi.|
|**-a** [processorName]! [directiveName]! \<parameterName> !\<parameterValue>|Yönerge işlemcisi için bir parametre değeri belirtin. Yalnızca parametre adını ve değerini belirtirsiniz, parametre tüm yönerge işlemcileri tarafından kullanılabilir. Bir yönerge işlemcisi belirtirsiniz, parametresi yalnızca belirtilen işlemci tarafından kullanılabilir. Bir yönerge adı belirtirsiniz, parametresi yalnızca belirtilen yönerge işlenirken kullanılabilir.<br /><br /> Parametre değerlerine yönerge işlemcisi veya metin şablonundan erişmek için [ITextTemplatingEngineHost.ResolveParameterValue kullanın.](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)) Bir metin şablonunda, şablon `hostspecific` yönergesine dahil edilir ve iletiyi üzerinde `this.Host` çağırır. Örnek:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> İsteğe bağlı işlemci ve yönerge adlarını atlasanız bile her zaman '!' işaretlerini yazın. Örnek:<br /><br /> `-a !!param!value`|
|**-h**|Yardım sağlar.|

## <a name="related-topics"></a>İlgili konular

|Görev|Konu|
|-|-|
|Bir çözümde Visual Studio oluşturma.|[T4 Metin Şablonları Kullanarak Tasarım Zamanı Kodu Oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Kendi veri kaynaklarınızı dönüştürmek için yönerge işlemcileri yazın.|[T4 Metin Dönüştürmeyi Özelleştirme](../modeling/customizing-t4-text-transformation.md)|
|Kendi uygulamanıza ait metin şablonlarını çağırmanıza olanak sağlayan bir metin şablon oluşturma ana bilgisayarı yazın.|[Bir Özel Konak kullanarak Metin Şablonlarını İşleme](../modeling/processing-text-templates-by-using-a-custom-host.md)|
