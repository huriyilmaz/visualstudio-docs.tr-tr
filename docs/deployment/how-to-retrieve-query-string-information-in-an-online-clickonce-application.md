---
title: çevrimiçi ClickOnce uygulamasında sorgu dize bilgilerini alma
description: bir ClickOnce uygulamasının bir URL 'nin sorgu bölümünü nasıl okuyabileceğinizi ve query dize parametrelerini kabul edecek şekilde uygulamanızı yapılandırmak için mageuı 'yi nasıl kullanacağınızı öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122089946"
---
# <a name="how-to-retrieve-query-string-information-in-an-online-clickonce-application"></a>nasıl yapılır: çevrimiçi ClickOnce uygulamasında sorgu dize bilgilerini alma
*Sorgu dizesi* , bir URL 'nin *adı = değer* biçiminde rastgele bilgiler içeren bir soru işareti (?) ile başlayan bölümüdür. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Üzerinde barındırdığınızı adlı bir uygulamanız olduğunu `WindowsApp1` `servername` ve uygulama başlatıldığında değişken için bir değer geçirmek istediğinizi varsayalım `username` . URL 'niz aşağıdakine benzer şekilde görünebilir:

 `http://servername/WindowsApp1.application?username=joeuser`

 Aşağıdaki iki yordamda [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sorgu dizesi bilgilerini elde etmek için bir uygulamanın nasıl kullanılacağı gösterilmektedir.

> [!NOTE]
> Yalnızca uygulamanız bir dosya paylaşımının veya yerel dosya sisteminin kullanılması yerine HTTP kullanarak başlatıldığında bir sorgu dizesinde bilgi geçirebilirsiniz.

 İlk yordam, uygulamanızın başlatıldığında [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bu değerleri okumak için küçük bir kod parçasını nasıl kullanabileceğinizi gösterir.

 Sonraki yordamda, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sorgu dizesi parametrelerini kabul edebilmesi için MageUI.exe kullanarak uygulamanızı yapılandırma gösterilmektedir. Uygulamanızı yayımladığınızda bunu yapmanız gerekir.

> [!NOTE]
> Bu özelliği etkinleştirme kararı vermeden önce bu konunun devamındaki "güvenlik" bölümüne bakın.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] *Mage.exe* veya *MageUI.exe* kullanarak dağıtım oluşturma hakkında daha fazla bilgi için bkz. [izlenecek yol: el ile ClickOnce uygulaması dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

> [!NOTE]
> .NET Framework 3,5 SP1 'den başlayarak, komut satırı bağımsız değişkenlerini çevrimdışı bir uygulamaya geçirmek mümkündür [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Uygulamaya bağımsız değişkenler sağlamak istiyorsanız, kısayol dosyasına parametreleri ile geçiş yapabilirsiniz. APPREF-MS uzantısı.

### <a name="to-obtain-query-string-information-from-a-clickonce-application"></a>ClickOnce uygulamasından sorgu dizesi bilgilerini almak için

1. Aşağıdaki kodu projenize yerleştirin. Bu kodun çalışması için, System. Web `using` `Imports` , System. Collections. özelleşmiş ve System. Deployment. Application için bir başvuruya sahip olmanız gerekir.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceQueryString/CS/Form1.cs" id="Snippet1":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceQueryString/VB/Form1.vb" id="Snippet1":::


2. <xref:System.Collections.DictionaryBase.Dictionary%2A>Ad ile dizine alınmış sorgu dizesi parametrelerini almak için daha önce tanımlanan işlevi çağırın.

### <a name="to-enable-query-string-passing-in-a-clickonce-application-with-mageuiexe"></a>ClickOnce bir uygulamada sorgu dizesi geçişini etkinleştirmek için MageUI.exe

1. .NET komut Istemi ' ni açın ve şunu yazın:

   ```cmd
   MageUI
   ```

2. **Dosya** menüsünde **Aç**' ı seçin ve uygulamanızın dağıtım bildirimini açın [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , bu dosya `.application` uzantıda sona eriyor.

3. Sol taraftaki Gezinti penceresinde **dağıtım seçenekleri** panelini SEÇIN ve **URL parametrelerinin uygulamaya geçirilmesine izin ver** onay kutusunu seçin.

4. **Dosya** menüsünde **Kaydet**' i seçin.

> [!NOTE]
> Alternatif olarak, sorgu dizesi geçişini de etkinleştirebilirsiniz [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] . **Project özellikler** açılarak, **yayımla** sekmesini seçerek, **seçenekler** düğmesine tıklayıp ve ardından **bildirimler**' i seçerek bulunan **URL parametrelerinin uygulamaya geçirilmesine izin ver** onay kutusunu seçin.

## <a name="robust-programming"></a>Güçlü programlama
 Sorgu dizesi parametreleri kullandığınızda uygulamanızın nasıl yüklendiğine ve etkinleştirilme konusunda dikkatli bir dikkat etmeniz gerekir. Uygulamanız kullanıcının bilgisayarına Web 'den veya bir ağ paylaşımından yüklenmek üzere yapılandırılmışsa, büyük olasılıkla Kullanıcı uygulamayı URL aracılığıyla yalnızca bir kez etkinleştirecektir. Bundan sonra, Kullanıcı **Başlangıç** menüsündeki kısayolunu kullanarak uygulamanızı genellikle etkinleştirir. Sonuç olarak, uygulamanız yaşam süresi boyunca yalnızca bir kez sorgu dizesi bağımsız değişkenlerini alacak şekilde garanti edilir. Gelecekte kullanılmak üzere bu bağımsız değişkenleri kullanıcının makinesinde depolamayı seçerseniz, bunları güvenli ve güvenli bir şekilde saklamaktan siz sorumlusunuz.

 Uygulamanız yalnızca çevrimiçi ise, her zaman bir URL aracılığıyla etkinleştirilir. Ancak, bu durumda bile sorgu dizesi parametreleri eksik veya bozuksa uygulamanızın düzgün çalışması için yazılması gerekir.

## <a name="net-framework-security"></a>.NET Framework güvenliği
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Yalnızca herhangi bir kötü amaçlı karakter girişini kullanmadan önce, UYGULAMANıZA URL parametreleri geçirilmesine izin verin. örneğin, tırnak işaretleri, eğik çizgi veya noktalı virgülle gömülü bir dize, bir veritabanında SQL sorgusunda filtrelenmemiş olarak kullanılırsa rastgele veri işlemleri gerçekleştirebilir. Sorgu dizesi güvenliği hakkında daha fazla bilgi için bkz. [komut dosyası kötüye bakış](/previous-versions/w1sw53ds(v=vs.140)).

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını koruma](../deployment/securing-clickonce-applications.md)