---
title: TextTransform yardımcı programı ile dosya oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
ms.assetid: 06a48235-fe02-403e-a1cf-2ae70b4db62f
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 18776795fdf693c855edd3f629d674089daaaebd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666091"
---
# <a name="generating-files-with-the-texttransform-utility"></a>TextTransform Yardımcı Programı ile Dosya Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TextTransform. exe, bir metin şablonunu dönüştürmek için kullanabileceğiniz bir komut satırı aracıdır. TextTransform. exe ' yi çağırdığınızda, bir metin şablonu dosyasının adını bağımsız değişken olarak belirtirsiniz. TextTransform. exe, metin dönüştürme altyapısını çağırır ve metin şablonunu işler. TextTransform. exe genellikle betiklerden çağırılır. Bununla birlikte, Visual Studio 'da veya yapı sürecinde metin dönüştürmesi gerçekleştirebildiğinden genellikle gerekli değildir.

> [!NOTE]
> Yapı işleminin bir parçası olarak metin dönüştürmesi gerçekleştirmek istiyorsanız, MSBuild metin dönüştürme görevini kullanmayı düşünün. Daha fazla bilgi için bkz. [derleme sürecinde kod oluşturma](../modeling/code-generation-in-a-build-process.md). @No__t_0 yüklü bir makinede, metin şablonlarını dönüştürebilen bir uygulama veya [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantısı da yazabilirsiniz. Daha fazla bilgi için bkz. [özel bir konak kullanarak metin şablonlarını işleme](../modeling/processing-text-templates-by-using-a-custom-host.md).

 TextTransform. exe aşağıdaki dizinde bulunur:

 **\Program Files\Common Files\Microsoft Shared\TextTemplating\11.0**

## <a name="syntax"></a>Sözdizimi

```
TextTransform [<options>] <templateName>
```

#### <a name="parameters"></a>Parametreler

|**Değişkendir**|**Açıklama**|
|------------------|---------------------|
|`templateName`|Dönüştürmek istediğiniz şablon dosyasının adını tanımlar.|

|**Seçeneği**|**Açıklama**|
|----------------|---------------------|
|**-out** \<filename >|Dönüşümün çıktısının yazıldığı dosya.|
|**-r** \<assembly >|Metin şablonunu derlemek ve çalıştırmak için kullanılan bir derleme.|
|**-u** \<namespace >|Şablonu derlemek için kullanılan bir ad alanı.|
|**-I** \<includedirectory >|Belirtilen metin şablonunda bulunan metin şablonlarını içeren bir dizin.|
|**-P** \<referencepath >|Metin şablonunda belirtilen derlemeleri aramak veya **-r** seçeneğinin kullanılması için bir dizin.<br /><br /> Örneğin, Visual Studio API için kullanılan derlemeleri dahil etmek için şunu kullanın<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName >! \<className >! \<assemblyName&#124;codebase >|Metin şablonu içinde özel yönergeleri işlemek için kullanılabilen bir yönerge işlemcisinin adı, tam tür adı ve derlemesi.|
|**-a** [ProcessorName]! [directiveName]! \<parameterName >! \<parameterValue >|Yönerge işlemcisi için bir parametre değeri belirtin. Yalnızca parametre adını ve değerini belirtirseniz parametre tüm yönerge işlemcileri tarafından kullanılabilir. Bir yönerge işlemcisi belirtirseniz, parametre yalnızca belirtilen işlemci için kullanılabilir. Bir yönerge adı belirtirseniz parametre yalnızca belirtilen yönerge işlenirken kullanılabilir.<br /><br />  Bir metin şablonunda, şablon yönergesine `hostspecific` ekleyin ve `this.Host` ileti çağırın. Örneğin:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> İsteğe bağlı işlemci ve yönerge adlarını atlarsanız bile her zaman '! ' işaretlerini yazın. Örneğin:<br /><br /> `-a !!param!value`|
|**-h**|Yardım sağlar.|

## <a name="related-topics"></a>İlgili konular

|Görev|Konu|
|----------|-----------|
|@No__t_0 çözümünde dosya oluşturun.|[T4 Metin Şablonları Kullanarak Tasarım Zamanı Kodu Oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Kendi veri kaynaklarınızı dönüştürmek için yönerge işlemcileri yazın.|[T4 Metin Dönüştürmeyi Özelleştirme](../modeling/customizing-t4-text-transformation.md)|
|Kendi uygulamanızdan metin şablonları çağırmanıza olanak sağlayan bir metin şablonu oluşturma Konağı yazın.|[Bir Özel Konak kullanarak Metin Şablonlarını İşleme](../modeling/processing-text-templates-by-using-a-custom-host.md)|
