---
title: Çevrimiçi uygulama içinde sorgu dizesi ClickOnce alma
description: Bir ClickOnce URL'nin sorgu bölümünü nasıl okuyabili ve MageUI kullanarak sorgu dizesi parametrelerini kabul etmek üzere uygulama yapılandırmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, query strings
- query strings, retrieving information
ms.assetid: 48ce098a-a075-481b-a5f5-c8ba11f63120
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 13a3a02b8853ede34ec257c01c0300e22fba136a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635265"
---
# <a name="how-to-retrieve-query-string-information-in-an-online-clickonce-application"></a>Nasıl yapılan: Çevrimiçi bir uygulamanın sorgu dizesi ClickOnce alma
Sorgu *dizesi,* form adı=değeri içinde rastgele bilgiler içeren bir soru işareti (?) ile başlayan BIR *URL'nin bölümü.* üzerinde barındırarak adlı bir uygulamanın olduğunu ve uygulama başlatan değişken için [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `WindowsApp1` bir değer geçmek `servername` `username` istediğinizi varsayalım. URL'niz aşağıdaki gibi olabilir:

 `http://servername/WindowsApp1.application?username=joeuser`

 Aşağıdaki iki yordam, sorgu dizesi bilgilerini almak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] için bir uygulamanın nasıl kullanıla bir olduğunu gösterir.

> [!NOTE]
> Bir sorgu dizesinde bilgileri yalnızca, dosya paylaşımı veya yerel dosya sistemi kullanmak yerine HTTP kullanılarak başlatıldıklarında gönderebilirsiniz.

 İlk yordam, uygulama başlatılana kadar bu değerleri okumak için uygulamanın nasıl küçük [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bir kod parçası kullanabileceğini gösterir.

 Sonraki yordamda, sorgu dizesi parametrelerini kabul etmek MageUI.exe kullanarak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamanın nasıl yapılandırıldığından emin olmak gerekir. Bu, uygulamayı her yayımlarken bunu yapmak gerekir.

> [!NOTE]
> Bu özelliği etkinleştirmeye karar vermeden önce bu konunun devamında yer alan "Güvenlik" bölümüne bakın.

 Mage.exeveyaMageUI.exekullanarak dağıtım oluşturma hakkında bilgi [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] *için,* bkz. [Walkthrough: Manually deploy a ClickOnce application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). 

> [!NOTE]
> 3.NET Framework 3.5 SP1'den başlayarak, komut satırı bağımsız değişkenlerini çevrimdışı bir uygulamaya [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] devredebilirsiniz. Uygulamaya bağımsız değişkenler sağlamak için parametreleri ile kısayol dosyasına geçebilirsiniz. APPREF-MS uzantısı.

### <a name="to-obtain-query-string-information-from-a-clickonce-application"></a>Bir uygulamanın sorgu dizesi bilgilerini ClickOnce için

1. Aşağıdaki kodu projenize girin. Bu kodun çalışması için System.Web başvurusuna sahip olmak ve `using` `Imports` System.Web, System.Collections.Specialized ve System.Deployment.Application için veya yönergeleri eklemeniz gerekir.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceQueryString/CS/Form1.cs" id="Snippet1":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceQueryString/VB/Form1.vb" id="Snippet1":::


2. Daha önce tanımlanan işlevini çağırarak <xref:System.Collections.DictionaryBase.Dictionary%2A> adla dizine alınan sorgu dizesi parametrelerini alın.

### <a name="to-enable-query-string-passing-in-a-clickonce-application-with-mageuiexe"></a>Sorgu dizesinin ClickOnce ile MageUI.exe

1. .NET Komut İstemi'ne yazın:

   ```cmd
   MageUI
   ```

2. Dosya **menüsünde Aç'ı** **seçin** ve uzantıyla biten dosya olan uygulamanın [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım bildirimini `.application` açın.

3. Sol **gezinti penceresinde** Dağıtım Seçenekleri panelini seçin ve URL parametrelerinin uygulamaya geçirilesine **izin ver onay** kutusunu seçin.

4. Dosya menüsünde **Kaydet'i** **seçin.**

> [!NOTE]
> Alternatif olarak, sorgu dizesi geçirmeyi [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] etkinleştirebilirsiniz. Url **parametrelerinin uygulamaya** geçirilene izin ver onay kutusunu seçin. Bu onay kutusu  Project Özellikler'i  açarak, Yayımla sekmesini seçerek, Seçenekler düğmesine tıklar ve ardından Bildirim'i  **seçerek bulunabilir.**

## <a name="robust-programming"></a>Güçlü programlama
 Sorgu dizesi parametrelerini kullanırken, uygulamanın nasıl yük devredildiğinde ve etkinleştirildiğinde dikkatli bir şekilde göz önünde bulundurulmalıdır. Uygulamanız kullanıcının bilgisayarına Web'den veya bir ağ paylaşımından yükecek şekilde yapılandırılmışsa, büyük olasılıkla kullanıcı uygulamayı URL aracılığıyla yalnızca bir kez etkinleştirir. Bundan sonra kullanıcı genellikle Başlat menüsündeki kısayolu kullanarak uygulamanızı **etkinleştirir.** Sonuç olarak, uygulamanın ömrü boyunca sorgu dizesi bağımsız değişkenlerini yalnızca bir kez alma garantisi vardır. Bu bağımsız değişkenleri daha sonra kullanmak üzere kullanıcının makinesine depolamayı seçerseniz, bunları güvenli ve güvenli bir şekilde depolamak sizin sorumluluğundadır.

 Uygulamanız yalnızca çevrimiçi ise, her zaman bir URL aracılığıyla etkinleştirilir. Ancak bu durumda bile sorgu dizesi parametreleri eksik veya bozuksa, uygulamanın düzgün çalışması için yazıldığı gerekir.

## <a name="net-framework-security"></a>.NET Framework güvenliği
 Url parametrelerini uygulamanıza yalnızca kötü [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] amaçlı karakterlerin girişini kullanmadan önce temizlemeyi planlıyorsanız geçirmenize izin ver. Örneğin, tırnak, eğik çizgi veya noktalı virgülle eklenmiş bir dize, veritabanındaki bir sorguda filtrelenmemiş SQL rastgele veri işlemleri gerçekleştirebilirsiniz. Sorgu dizesi güvenliği hakkında daha fazla bilgi için bkz. Betik [açıklarından yararlanmaya genel bakış.](/previous-versions/w1sw53ds(v=vs.140))

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını koruma](../deployment/securing-clickonce-applications.md)