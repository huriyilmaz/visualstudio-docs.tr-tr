---
title: TextTransform Yardımcı Programı ile Dosya Oluşturma
description: TextTransform yardımcı programının bir metin şablonunu dönüştürmek için kullanabileceğiniz bir komut satırı aracı olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 07/26/2019
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 743b7deb118bb3506773ec1a82d2331633afa7bc
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388834"
---
# <a name="generate-files-with-the-texttransform-utility"></a>TextTransform yardımcı programı ile dosya oluşturma

TextTransform.exe, bir metin şablonunu dönüştürmek için kullanabileceğiniz bir komut satırı aracıdır. TextTransform.exe çağırdığınızda, bir metin şablonu dosyasının adını bağımsız değişken olarak belirtirsiniz. TextTransform.exe metin dönüştürme altyapısını çağırır ve metin şablonunu işler. TextTransform.exe genellikle betiklerden çağırılır. Bununla birlikte, Visual Studio 'da veya yapı sürecinde metin dönüştürmesi gerçekleştirebildiğinden genellikle gerekli değildir.

> [!NOTE]
> Yapı işleminin bir parçası olarak metin dönüştürmesi gerçekleştirmek istiyorsanız, MSBuild metin dönüştürme görevini kullanmayı düşünün. Daha fazla bilgi için bkz. [derleme sürecinde kod oluşturma](../modeling/code-generation-in-a-build-process.md). Visual Studio 'Nun yüklü olduğu bir makinede, metin şablonlarını dönüştürebilen bir uygulama veya Visual Studio uzantısı da yazabilirsiniz. Daha fazla bilgi için bkz. [özel bir konak kullanarak metin şablonlarını işleme](../modeling/processing-text-templates-by-using-a-custom-host.md).

TextTransform.exe aşağıdaki dizinde bulunur:

::: moniker range=">=vs-2019"

**\Program Files (x86) \Microsoft Visual Studio\2019\Professional\Common7\IDE**

Professional Edition veya

**\Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE**

Enterprise Edition için.

::: moniker-end

::: moniker range="vs-2017"

**\Program Files (x86) \Microsoft Visual Studio\2017\Professional\Common7\IDE**

Professional Edition veya

**\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

Enterprise Edition için.

Visual Studio 'nun önceki sürümlerinde, dosya aşağıdaki konumda bulunur:

**\Program Files (x86) \Common Files\Microsoft Shared\textşablon oluşturma \{ sürümü}**

burada {Version}, hangi önceki sürümün yüklü olduğuna bağlıdır.

::: moniker-end

## <a name="syntax"></a>Sözdizimi

```
TextTransform [<options>] <templateName>
```

### <a name="parameters"></a>Parametreler

|**Değişkendir**|**Açıklama**|
|-|-|
|`templateName`|Dönüştürmek istediğiniz şablon dosyasının adını tanımlar.|

|**Seçenek**|**Açıklama**|
|-|-|
|**-Out**\<filename>|Dönüşümün çıktısının yazıldığı dosya.|
|**-r**\<assembly>|Metin şablonunu derlemek ve çalıştırmak için kullanılan bir derleme.|
|**-u**\<namespace>|Şablonu derlemek için kullanılan bir ad alanı.|
|**-I**\<includedirectory>|Belirtilen metin şablonunda bulunan metin şablonlarını içeren bir dizin.|
|**-P**\<referencepath>|Metin şablonunda belirtilen derlemeleri aramak veya **-r** seçeneğinin kullanılması için bir dizin.<br /><br /> Örneğin, Visual Studio API için kullanılan derlemeleri dahil etmek için şunu kullanın<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-DP** \<processorName> ! \<className> !\<assemblyName&#124;codeBase>|Metin şablonu içinde özel yönergeleri işlemek için kullanılabilen bir yönerge işlemcisinin adı, tam tür adı ve derlemesi.|
|**-a** [ProcessorName]! [directiveName]! \<parameterName> !\<parameterValue>|Yönerge işlemcisi için bir parametre değeri belirtin. Yalnızca parametre adını ve değerini belirtirseniz parametre tüm yönerge işlemcileri tarafından kullanılabilir. Bir yönerge işlemcisi belirtirseniz, parametre yalnızca belirtilen işlemci için kullanılabilir. Bir yönerge adı belirtirseniz parametre yalnızca belirtilen yönerge işlenirken kullanılabilir.<br /><br /> Yönerge işlemcisi veya metin şablonundan parametre değerlerine erişmek için [ITextTemplatingEngineHost. ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\))kullanın. Bir metin şablonunda, `hostspecific` şablon yönergesine dahil edin ve iletiyi üzerine çağırın `this.Host` . Örneğin:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> İsteğe bağlı işlemci ve yönerge adlarını atlarsanız bile her zaman '! ' işaretlerini yazın. Örneğin:<br /><br /> `-a !!param!value`|
|**-h**|Yardım sağlar.|

## <a name="related-topics"></a>İlgili konular

|Görev|Konu|
|-|-|
|Visual Studio çözümünde dosya oluşturun.|[T4 Metin Şablonları Kullanarak Tasarım Zamanı Kodu Oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Kendi veri kaynaklarınızı dönüştürmek için yönerge işlemcileri yazın.|[T4 Metin Dönüştürmeyi Özelleştirme](../modeling/customizing-t4-text-transformation.md)|
|Kendi uygulamanızdan metin şablonları çağırmanıza olanak sağlayan bir metin şablonu oluşturma Konağı yazın.|[Bir Özel Konak kullanarak Metin Şablonlarını İşleme](../modeling/processing-text-templates-by-using-a-custom-host.md)|
