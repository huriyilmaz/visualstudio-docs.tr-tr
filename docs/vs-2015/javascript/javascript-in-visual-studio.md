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
ms.openlocfilehash: 175cb6f6a8a3f240c244e139406841b0546209cc
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295903"
---
# <a name="javascript-in-visual-studio"></a>Visual Studio’da JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript, Visual Studio'da birinci sınıf bir dildir. Visual Studio IDE'de JavaScript kodu yazarken standart düzenleme yardımlarının (kod parçacıkları, IntelliSense, vb.) çoğunu veya tümünü kullanabilirsiniz. Birçok uygulama türleri ve hizmetler için JavaScript kodu yazabilirsiniz.

 JavaScript dil başvurusu belgeleri için bkz. [JavaScript](https://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx).

 Belirli uygulama türlerini ve HTML ve JavaScript kullanarak hizmetleri geliştirmek için Visual Studio ya da belirli Visual Studio uzantıları belirli sürümlerini gerekebilir. Aşağıdaki listede, daha fazla bilgi için bağlantılar içerir.

- Apache Cordova kullanarak platformlar arası uygulamalar oluşturmak için [Apache Cordova Visual Studio Araçları alın](https://go.microsoft.com/fwlink/p/?LinkId=397606).

- [Windows Mağazası](https://developer.microsoft.com/), [Windows Phone](https://developer.microsoft.com/)ve evrensel uygulamalar (her iki platformu da destekler) oluşturmak için [Araçları alın](https://developer.microsoft.com/windows/downloads).

- Bulut tabanlı hizmetler oluşturmak için [Microsoft Azure sitesine](https://azure.microsoft.com/documentation/)bakın.

- Web siteleri ve Web uygulamaları oluşturmak için [ASP.net sitesine bakın](https://dotnet.microsoft.com/apps/aspnet/web-apps).

  > [!NOTE]
  > Boş bir ASP.Net Web sitesi oluşturabileceğinizi ve HTML, CSS ve JavaScript programlama için kullanın. Visual Studio'da hata ayıklama ASP.NET tarafından sağlanan Webconfig dosyası etkinleştirir (veya uygulamayı çalıştırdığınızda F12 araçları da kullanabilirsiniz).

  Visual Studio'daki JavaScript düzenleyicisi IntelliSense desteği sunar. Daha fazla bilgi için bkz. [JavaScript IntelliSense](../ide/javascript-intellisense.md).

## <a name="whats-new-in-javascript"></a>Javascript'teki Yenilikler
 Yeni JavaScript özellikleri, aşağıdaki tabloda listelenmiştir.

|Özellik|Açıklama|
|-------------|-----------------|
|Sınıflar|Yeni sözdizimi [sınıfların](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/class)bildirimini destekler.|
|Gösterir|Bu, daha kolay ve temizleyici zaman uyumsuz [kodlamaya izin verir](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) . Promise oluşturucuları, `all` ve `race` yardımcı program yöntemleriyle birlikte desteklenir.|
|Yineleyiciler|Artık her ayrı bir özellik değeri için çalıştırılacak deyimleri ile bir özel yineleme kancası çağırma (diziler, dizi benzeri nesneleri ve yineleyiciler dahil) iterable nesneler üzerinde yineleyebilirsiniz. Daha fazla bilgi için bkz. [yineleyiciler ve](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Iterators_and_Generators)oluşturucular. **Note:**  Oluşturucular henüz desteklenmiyor.|
|Ok işlevleri|Ok işlevi (= >), bir sözcük temelli `this` bağlamayı sunan `function` anahtar sözcüğü için toplu bir sözdizimi sağlar.|
|Yerleşik nesneler için yeni yöntemler|[Dizi nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array), [matematik nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Math), [sayı nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number), [nesne nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)ve [dize nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String) yerleşik nesneleri, verileri yönetmek ve incelemek için birçok yeni yardımcı program işlevlerini ve özelliklerini içerir.|
|Nesne sabit değeri geliştirmeleri|Nesneler artık hesaplanan özellikler, kısa yöntemi tanımları ve toplu değer sözdizimi değeri için aynı adlı bir değişken başlatılır özellikleri destekler. Daha fazla bilgi için bkz. [nesne oluşturma](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object).|
|Proxy'ler|[Proxy 'ler](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Proxy) nesneler için özel davranışı etkinleştirir.|
|REST parametreleri|REST parametreler ardışık bağımsız değişken bir dizi işlev çağrısında olanak sağlar. Daha fazla bilgi için bkz. [işlevler](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function).|
|Spread işleci|[Yay işleci](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Spread_operator) (`…`) yinelenebilir ifadeleri bağımsız bağımsız değişkenlere genişletir. Örneğin, `a.b(…array)` `a.b.apply(a, array)`yaklaşık olarak aynı.|
|Simgeleri|[Sembol](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Symbol) nesneleri, özelliklerin mevcut nesne özellikleriyle, hiçbir istenmeyen görünürlük olmadan ve diğer kodun koordine edilmemiş eklemeleri olmadan var olan nesnelere eklenmesine izin verir.|
|Şablon dizeleri|[Şablon dizeleri](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Template_literals) , ifadelerin değerlendirilme ve dize sabiti ile bitiştirilmesine izin veren dize sabit değerleri.|
|Unicode geliştirmeleri|Geliştirmeler yapılmıştır Unicode desteği. Örneğin, yeni bir kaçış dizisi biçimi astral kod noktası (dörtten fazla onaltılı basamaklar içeren kod noktaları) destekler. Daha fazla bilgi için bkz. [özel karakterler](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Regular_Expressions#Types_of_special_characters).|
|WeakSet|[WeakSet](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/WeakSet) , başka herhangi bir yerde başvurulmadıklarında atık olarak toplanabilecek nesneler koleksiyonudur.|
