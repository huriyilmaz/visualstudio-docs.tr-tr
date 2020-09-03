---
title: JavaScript
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-javascript
ms.topic: conceptual
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 778912c3149f9f146c01dbab15afa4fabeaa49b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852253"
---
# <a name="javascript-in-visual-studio"></a>Visual Studio’da JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript, Visual Studio 'da birinci sınıf bir dildir. Visual Studio IDE'de JavaScript kodu yazarken standart düzenleme yardımlarının (kod parçacıkları, IntelliSense, vb.) çoğunu veya tümünü kullanabilirsiniz. Birçok uygulama türü ve hizmeti için JavaScript kodu yazabilirsiniz.

 JavaScript dil başvurusu belgeleri için bkz. [JavaScript](https://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx).

 Visual Studio 'nun belirli sürümleri veya belirli Visual Studio uzantıları, HTML ve JavaScript kullanarak belirli uygulama türlerini ve hizmetlerini geliştirmek için gerekli olabilir. Aşağıdaki listede daha fazla bilgi için bağlantılar bulunur.

- Apache Cordova kullanarak platformlar arası uygulamalar oluşturmak için [Apache Cordova Visual Studio Araçları alın](https://taco.visualstudio.com/docs/install-vs-tools-apache-cordova/).

- [Windows Mağazası](https://developer.microsoft.com/), [Windows Phone](https://developer.microsoft.com/)ve evrensel uygulamalar (her iki platformu da destekler) oluşturmak için [Araçları alın](https://developer.microsoft.com/windows/downloads).

- Bulut tabanlı hizmetler oluşturmak için [Microsoft Azure sitesine](https://azure.microsoft.com/documentation/)bakın.

- Web siteleri ve Web uygulamaları oluşturmak için [ASP.net sitesine bakın](https://dotnet.microsoft.com/apps/aspnet/web-apps).

  > [!NOTE]
  > Boş bir ASP.Net Web sitesi oluşturabilir ve bunu HTML, CSS ve JavaScript programlama için kullanabilirsiniz. ASP.NET tarafından sunulan Webconfig dosyası, Visual Studio 'da hata ayıklamayı sağlar (veya uygulamayı çalıştırdığınızda F12 araçlarını kullanabilirsiniz).

  Visual Studio'daki JavaScript düzenleyicisi IntelliSense desteği sunar. Daha fazla bilgi için bkz. [JavaScript IntelliSense](../ide/javascript-intellisense.md).

## <a name="whats-new-in-javascript"></a>Javascript'teki Yenilikler
 JavaScript için yeni özellikler aşağıdaki tabloda listelenmiştir.

|Özellik|Açıklama|
|-------------|-----------------|
|Sınıflar|Yeni sözdizimi [sınıfların](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/class)bildirimini destekler.|
|Aşmayı taahhüt eder|Bu, daha kolay ve temizleyici zaman uyumsuz [kodlamaya izin verir](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) . Promise oluşturucuları, `all` ve `race` yardımcı yöntemleriyle birlikte desteklenir.|
|Yineleyiciler|Artık tekrarlanamayacak nesneler (diziler, dizi benzeri nesneler ve yineleyiciler dahil) üzerinde yineleyebilir, her ayrı özelliğin değeri için yürütülecek deyimlerle özel bir yineleme kancası çağırarak. Daha fazla bilgi için bkz. [yineleyiciler ve](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Iterators_and_Generators)oluşturucular. **Note:**  Oluşturucular henüz desteklenmiyor.|
|Ok işlevleri|Ok işlevi (=>), `function` sözcük temelli bağlama özelliklerinin kullanıldığı anahtar sözcüğü için kısayol söz dizimi sağlar `this` .|
|Yerleşik nesneler için yeni Yöntemler|[Dizi nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array), [matematik nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Math), [sayı nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number), [nesne nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)ve [dize nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String) yerleşik nesneleri, verileri yönetmek ve incelemek için birçok yeni yardımcı program işlevlerini ve özelliklerini içerir.|
|Nesne değişmez değeri geliştirmeleri|Nesneler artık hesaplanan özellikleri, kısa yöntem tanımlarını ve değeri aynı adlı bir değişkene başlatılan özellikler için kısayol söz dizimini desteklemektedir. Daha fazla bilgi için bkz. [nesne oluşturma](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object).|
|Kullanıldığı|[Proxy 'ler](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Proxy) nesneler için özel davranışı etkinleştirir.|
|Rest parametreleri|Rest parametreleri, bir dizi işlev çağrısında ardışık bağımsız değişkenleri açmanızı sağlar. Daha fazla bilgi için bkz. [işlevler](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function).|
|Yay işleci|[Yay işleci](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Spread_operator) ( `…` ) yinelenebilir ifadeleri bağımsız bağımsız değişkenlere genişletir. Örneğin, `a.b(…array)` yaklaşık olarak aynı `a.b.apply(a, array)` .|
|Simgeleri|[Sembol](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Symbol) nesneleri, özelliklerin mevcut nesne özellikleriyle, hiçbir istenmeyen görünürlük olmadan ve diğer kodun koordine edilmemiş eklemeleri olmadan var olan nesnelere eklenmesine izin verir.|
|Şablon dizeleri|[Şablon dizeleri](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Template_literals) , ifadelerin değerlendirilme ve dize sabiti ile bitiştirilmesine izin veren dize sabit değerleri.|
|Unicode geliştirmeleri|Unicode desteğiyle geliştirmeler yapılmıştır. Örneğin, yeni bir kaçış sırası biçimi Astral kod noktalarını destekler (dörtten fazla onaltılı basamak içeren kod noktaları). Daha fazla bilgi için bkz. [özel karakterler](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Regular_Expressions#Types_of_special_characters).|
|WeakSet|[WeakSet](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/WeakSet) , başka herhangi bir yerde başvurulmadıklarında atık olarak toplanabilecek nesneler koleksiyonudur.|
