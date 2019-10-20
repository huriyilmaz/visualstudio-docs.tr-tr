---
title: Çevrimiçi ClickOnce uygulamasında sorgu dize bilgilerini alma
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 30169a43d88f0ee8ae2c428e5a3da0aef0b9d642
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637857"
---
# <a name="how-to-retrieve-query-string-information-in-an-online-clickonce-application"></a>Nasıl yapılır: çevrimiçi bir ClickOnce uygulamasında sorgu dize bilgilerini alma
*Sorgu dizesi* , bir URL 'nin *adı = değer*biçiminde rastgele bilgiler içeren bir soru işareti (?) ile başlayan bölümüdür. @No__t_2 barındırdığınızı `WindowsApp1` adlı bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamanız olduğunu ve uygulama başlatıldığında `username` değişken için bir değer geçirmek istediğinizi varsayalım. URL 'niz aşağıdakine benzer şekilde görünebilir:

 `http://servername/WindowsApp1.application?username=joeuser`

 Aşağıdaki iki yordamda sorgu dizesi bilgilerini almak için bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamasının nasıl kullanılacağı gösterilmektedir.

> [!NOTE]
> Yalnızca uygulamanız bir dosya paylaşımının veya yerel dosya sisteminin kullanılması yerine HTTP kullanarak başlatıldığında bir sorgu dizesinde bilgi geçirebilirsiniz.

 İlk yordam, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamanızın uygulama başlatıldığında bu değerleri okumak için küçük bir kod parçasını nasıl kullanabileceğinizi gösterir.

 Sonraki yordamda, Query dize parametrelerini kabul edebilmesi için MageUI. exe kullanarak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamanızın nasıl yapılandırılacağı gösterilmektedir. Uygulamanızı yayımladığınızda bunu yapmanız gerekir.

> [!NOTE]
> Bu özelliği etkinleştirme kararı vermeden önce bu konunun devamındaki "güvenlik" bölümüne bakın.

 *Mage. exe* veya *MageUI. exe*kullanarak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtımı oluşturma hakkında daha fazla bilgi Için bkz. [izlenecek yol: el ile bir ClickOnce uygulaması dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

> [!NOTE]
> .NET Framework 3,5 SP1 'den başlayarak, komut satırı bağımsız değişkenlerini çevrimdışı bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamasına geçirmek mümkündür. Uygulamaya bağımsız değişkenler sağlamak istiyorsanız, kısayol dosyasına parametreleri ile geçiş yapabilirsiniz. APPREF-MS uzantısı.

### <a name="to-obtain-query-string-information-from-a-clickonce-application"></a>Sorgu dizesi bilgilerini bir ClickOnce uygulamasından almak için

1. Aşağıdaki kodu projenize yerleştirin. Bu kodun çalışması için System. Web 'e başvurunuz ve System. Web, System. Collections. özelleşmiş ve System. Deployment. Application için `using` ya da `Imports` yönergeleri eklemeniz gerekecektir.

     [!code-csharp[ClickOnceQueryString#1](../deployment/codesnippet/CSharp/how-to-retrieve-query-string-information-in-an-online-clickonce-application_1.cs)]
     [!code-vb[ClickOnceQueryString#1](../deployment/codesnippet/VisualBasic/how-to-retrieve-query-string-information-in-an-online-clickonce-application_1.vb)]

2. Ad ile dizine alınmış sorgu dizesi parametrelerinin <xref:System.Collections.DictionaryBase.Dictionary%2A> almak için daha önce tanımlanan işlevi çağırın.

### <a name="to-enable-query-string-passing-in-a-clickonce-application-with-mageuiexe"></a>MageUI. exe ile ClickOnce uygulamasında sorgu dizesi geçişini etkinleştirmek için

1. .NET komut Istemi ' ni açın ve şunu yazın:

   ```cmd
   MageUI
   ```

2. **Dosya** menüsünde **Aç**' ı seçin ve [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamanızın dağıtım bildirimini açın, bu dosya `.application` uzantısında sona eriyor.

3. Sol taraftaki Gezinti penceresinde **dağıtım seçenekleri** panelini SEÇIN ve **URL parametrelerinin uygulamaya geçirilmesine izin ver** onay kutusunu seçin.

4. **Dosya** menüsünde **Kaydet**' i seçin.

> [!NOTE]
> Alternatif olarak, [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] sorgu dizesi geçişini etkinleştirebilirsiniz. **Proje özellikleri**açılarak, **Yayımla** sekmesini seçerek, **Seçenekler** düğmesine tıklayıp ve ardından **Bildirimler**' i seçerek bulunan **URL parametrelerinin uygulamaya geçirilmesine izin ver** onay kutusunu seçin.

## <a name="robust-programming"></a>Güçlü programlama
 Sorgu dizesi parametreleri kullandığınızda uygulamanızın nasıl yüklendiğine ve etkinleştirilme konusunda dikkatli bir dikkat etmeniz gerekir. Uygulamanız kullanıcının bilgisayarına Web 'den veya bir ağ paylaşımından yüklenmek üzere yapılandırılmışsa, büyük olasılıkla Kullanıcı uygulamayı URL aracılığıyla yalnızca bir kez etkinleştirecektir. Bundan sonra, Kullanıcı **Başlangıç** menüsündeki kısayolunu kullanarak uygulamanızı genellikle etkinleştirir. Sonuç olarak, uygulamanız yaşam süresi boyunca yalnızca bir kez sorgu dizesi bağımsız değişkenlerini alacak şekilde garanti edilir. Gelecekte kullanılmak üzere bu bağımsız değişkenleri kullanıcının makinesinde depolamayı seçerseniz, bunları güvenli ve güvenli bir şekilde saklamaktan siz sorumlusunuz.

 Uygulamanız yalnızca çevrimiçi ise, her zaman bir URL aracılığıyla etkinleştirilir. Ancak, bu durumda bile sorgu dizesi parametreleri eksik veya bozuksa uygulamanızın düzgün çalışması için yazılması gerekir.

## <a name="net-framework-security"></a>.NET Framework güvenliği
 Yalnızca herhangi bir kötü amaçlı karakteri kullanmadan önce girişi temizlemeyi planlıyorsanız [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamanıza URL parametreleri geçirilmesine izin verin. Örneğin, tırnak işaretleri, eğik çizgi veya noktalı virgülle gömülü bir dize, bir SQL sorgusunda bir veritabanında filtrelenmemiş olarak kullanılırsa rastgele veri işlemleri gerçekleştirebilir. Sorgu dizesi güvenliği hakkında daha fazla bilgi için bkz. [komut dosyası kötüye bakış](https://msdn.microsoft.com/Library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07).

## <a name="see-also"></a>Ayrıca bkz.
- [Güvenli ClickOnce uygulamaları](../deployment/securing-clickonce-applications.md)
