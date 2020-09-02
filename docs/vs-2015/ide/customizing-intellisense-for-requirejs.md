---
title: RequireJS için IntelliSense 'i özelleştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 2be07ef8-9c08-444b-a21a-22a4fe6386a3
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 279ac7737460c90f86918ae673e8f64ef1215546
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665890"
---
# <a name="customizing-intellisense-for-requirejs"></a>RequireJS için IntelliSense'i özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2013 Güncelleştirme 4 başlayarak, popüler RequireJS JavaScript dosyası ve modüler yükleyici için destek desteklenir. RequireJS, kod modülleri arasında bağımlılıklar tanımlamanızı ve yalnızca gerektiğinde modülleri dinamik olarak yüklemeyi kolaylaştırır. RequireJS kullanan JavaScript kodu yazarken, modül tanımınızdan başvurduğunuz veya kodunuzun içinden yapılan çağrılar kullanılarak başvurulan modüller için IntelliSense önerileri sağlanacaktır `require()` .

 Varsayılan olarak, Visual Studio, RequireJS 'yi desteklemek için çok temel bir yapılandırmayı destekler, ancak kendi özel yapılandırma ayarlarınızı (kitaplıklar için diğer adlar tanımlamak için) ayarlama yaygın bir uygulamadır. Bu konuda, Visual Studio 'Yu projenizin benzersiz kurulumuyla çalışacak şekilde özelleştirebilmeniz için kullanabileceğiniz farklı yollar açıklanmaktadır.

 Bu konuda aşağıdakiler açıklanmaktadır:

- ASP.NET projelerinde RequireJS 'yi özelleştirme

- Apache Cordova uygulamalar, Windows Mağazası uygulamaları ve LightSwitch HTML uygulamaları oluşturmak için kullanılan JSProj projelerinde RequireJS ' yi özelleştirin

## <a name="customize-requirejs-in-aspnet-projects"></a>ASP.NET projelerinde RequireJS 'yi özelleştirme
 Geçerli JavaScript dosyanız tarafından require.js adlı bir dosya başvurulduğu zaman, RequireJS desteği otomatik olarak etkinleştirilir (daha fazla bilgi Için bkz. [JavaScript IntelliSense](../ide/javascript-intellisense.md)'de IntelliSense bağlamını belirleme bölümü). ASP.NET projelerinde, require.js başvuru genellikle _references.js bir dosya içinde bir/// \<reference/> yönergesi kullanılarak yapılır.

### <a name="configure-the-data-main-attribute-in-an-aspnet-project"></a>ASP.NET projesindeki Data-Main özniteliğini yapılandırma
 Uygulamanızı çalıştırdığınızda uygulamanızın nasıl çalışacağını doğru bir şekilde taklit etmek için, JavaScript düzenleyicisinin require.js ayarlarken önce hangi dosyanın yükleneceğini bilmesini gerektirir. Bu genellikle `data-main` , burada gösterildiği gibi, komut dosyası öğesindeki require.js başvuran özniteliği kullanılarak uygulama HTML dosyanızda yapılandırılır.

```html
<script src="js/require.js" data-main="js/app.js"></script>
```

 Bu örnekte, Data-Main (js/app.js) tarafından başvurulan betik, require.js sonra hemen yüklenir. Hemen yüklenen dosya, önce RequireJS kullanımını (kullanarak) yapılandırmak için en iyi yerdir `require.config()` . JavaScript düzenleyicisine uygulamanızdaki için kullanılacak dosyayı söylemek için `data-main` bir `data-main` öznitelik ekleyin ve ardından uygulamanızdaki require.js başvuran bir/// \<reference/> yönergesini değiştirin. Örneğin, bu yönergeyi kullanabilirsiniz:

```javascript
/// <reference path="js/require.js" data-main="js/app.js" />
```

### <a name="configure-the-application-start-page-in-an-aspnet-project"></a>Bir ASP.NET projesindeki uygulama başlangıç sayfasını yapılandırma
 Uygulama çalıştığında, RequireJS dosyalara göreli yolların (örneğin, ".. \\ " yollar) require.js Kitaplığı yükleyen HTML dosyasına göreli olduğunu varsayar. Bir ASP.NET projesi için Visual Studio Düzenleyicisi 'nde kod yazarken, bu başlangıç sayfası bilinmez ve göreli dosya yollarını kullanırken düzenleyiciye hangi başlangıç sayfasına başvuracaklarını söylemeniz gerekir. Bunu yapmak için `start-page` ///yönergesine bir öznitelik ekleyin \<reference/> .

```javascript
/// <reference path="js/require.js" data-main="js/app.js" start-page="/app/index.html" />
```

 `start-page`Özniteliği, uygulamanızı çalıştırırken bir tarayıcıda gördüğünüz gibi SAYFANıN URL 'sini belirtir.

## <a name="customize-requirejs-in-jsproj-projects"></a>JSProj projelerinde RequireJS 'yi özelleştirme
 JSProj projeleri (bir. JSProj Uzantısı ile biten proje dosyaları), Apache Cordova, HTML tabanlı Windows Mağazası uygulamaları veya LightSwitch HTML uygulamaları için uygulama oluştururken kullanılır. ASP.NET projelerinin aksine, bu projeler, projedeki mevcut olan HTML dosyalarından. js dosyalarına başvuruları okur. Bu nedenle, bir JSProj projesinde JavaScript 'ı düzenlediğinizde, şu anda düzenlenmekte olan JavaScript dosyasına require.js başvuruda bulunan başka bir HTML dosyasında başvuruluyorsa, RequireJS desteğinin etkinleştirildiğini görürsünüz.

 ASP.NET projeleri için gereken özelleştirme adımları bir JSProj proje dosyasında gerekli değildir. Diğer bir deyişle, `data-main` require.js başvuruda bulunan betik etiketinde özniteliği tarafından kullanılan komut dosyaları require.js yapılandırmak için otomatik olarak yüklenir. require.js başvuran HTML dosyası, uygulamanın başlangıç sayfası olarak da kullanılır.

## <a name="see-also"></a>Ayrıca Bkz.
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)
