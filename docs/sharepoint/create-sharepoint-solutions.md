---
title: SharePoint çözümleri oluşturma | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e1e5be38d0d44912052466162abaaa496c608d27
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981303"
---
# <a name="create-sharepoint-solutions"></a>SharePoint çözümleri oluşturma
  SharePoint Designer 'da oluşturmaya alternatif olarak, Visual Studio 'da SharePoint uygulamaları oluşturabilirsiniz. Visual Studio, gelişmiş hata ayıklama araçları, IntelliSense, ekstre tamamlama ve proje şablonları gibi özellikleri sağlayarak hızlı SharePoint geliştirmesini yükseltir. Visual Studio, gelişmiş .NET Framework tabanlı araç ve dillerden de yararlanır. Visual Basic veya görseli C#kullanarak SharePoint projeleri geliştirebilir ve JavaScript kullanarak SharePoint projeleri için uygulama geliştirebilirsiniz.

 SharePoint 2013 ve SharePoint eklentileri hakkında daha fazla bilgi için bkz. SharePoint [2013](https://products.office.com/previous-versions/microsoft-sharepoint-2013) ve SharePoint [için uygulama oluşturma](/sharepoint/dev/sp-add-ins/sharepoint-add-ins).

> [!NOTE]
> Yeni [SharePoint eklentisi modelinin](/sharepoint/dev/sp-add-ins/sharepoint-add-ins) , kullanıcılarınızın SharePoint deneyimini uzatmak için nasıl kullanılacağını öğrenin. Bu eklentiler, SharePoint çözümlerine kıyasla çok küçük bir baskı yazdırır ve HTML5, JavaScript, CSS3 ve XML gibi neredeyse her türlü Web programlama teknolojisini kullanarak bunları oluşturabilirsiniz.

|||
|-|-|
|![Belgeler](../sharepoint/media/vs-icon-documentation.gif "Belgeler")|**Belgeler**<br /><br /> [Visual Studio &#40;&#41; 'da -   kullanmaya başlama SharePoint geliştirmesini öğrenin](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)<br />-   [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)<br />-   [SharePoint çözümlerini yerelleştirin](../sharepoint/localizing-sharepoint-solutions.md)<br />[SharePoint çözümlerini derleme ve hata ayıklama](../sharepoint/building-and-debugging-sharepoint-solutions.md) -   <br />-   [paketleme ve SharePoint çözümlerini dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)<br />[Visual Studio 'Da SharePoint araçlarını genişletmek](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md) -   |
|![Belgeler](../sharepoint/media/vs-icon-documentation.gif "Belgeler")|**Öne çıkan görevler**<br /><br /> -   [Izlenecek yol: SharePoint için site sütunu, içerik türü ve liste oluşturma](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)<br />-   [nasıl yapılır: olay alıcısı oluşturma](../sharepoint/how-to-create-an-event-receiver.md)<br />-   [nasıl yapılır: BDC modeli oluşturma](../sharepoint/how-to-create-a-bdc-model.md)<br />-   [nasıl yapılır: SharePoint Web Bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part.md)<br />-   [nasıl yapılır: SharePoint uygulama sayfası veya Web Bölümü Için Kullanıcı denetimi oluşturma](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|
|![İzlenecek yollar](../sharepoint/media/vs-icon-walkthroughs.gif "İzlenecek Yollar")|**İzlenecek yollar**<br /><br /> -   [SharePoint geliştirme talimatları](../sharepoint/sharepoint-development-walkthroughs.md)|
|![Kod örnekleri](../sharepoint/media/vs-icon-codesamples.gif "Kod Örnekleri")|**Kod örnekleri**<br /><br /> -   [SharePoint geliştirme örnekleri](../sharepoint/sharepoint-development-samples.md)<br />-   [SharePoint Geliştirici İndirmeleri](/sharepoint/dev/)|
|![İtme](../sharepoint/media/vs-icon-training.gif "İtme")|**İtme**<br /><br /> -   [SharePoint geliştirme hakkında bilgi edinin](/sharepoint/dev/)|
|![Forumları](../sharepoint/media/vs-icon-forums.gif "Forumlar")|**Forumları**<br /><br /> [Visual Studio Ile SharePoint geliştirme](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vssharepointdevelopment) -   <br />-   [SharePoint 2010](https://social.msdn.microsoft.com/Forums/sharepoint/home?category=sharepoint2010,sharepoint)|
|![İtme](../sharepoint/media/vs-icon-training.gif "İtme")|**Bloglar**<br /><br /> [Visual Studio SharePoint geliştirme blogu](https://blogs.msdn.microsoft.com/vssharepointtoolsblog/) -   |
|![Nasıl yapılır? Larınız](../sharepoint/media/vs-icon-howdoivideos.gif "Nasıl yapılır? Larınız")|**Nasıl yapılır? Larınız**<br /><br /> -   [nasıl yaparım: Visual Studio 2010 ' de SharePoint 2010 Için visual Web bölümleri oluşturma](https://visualstudio.microsoft.com/)<br />-   [nasıl yaparım: Visual Studio 2010 ' de SharePoint 2010 Için Içerik türleri oluşturma?](/previous-versions/visualstudio/visual-studio-2010/dd831853\(v\=vs.100\))<br />-   [nasıl yaparım: Visual Studio 2010 ' de SharePoint 2010 Için site tanımları oluşturma?](/previous-versions/visualstudio/visual-studio-2010/dd831853\(v\=vs.100\))<br />-   [nasıl yaparım: Visual Studio 2010 kullanarak SharePoint 2010 için bir Iş verileri bağlantı modeli oluşturma](/previous-versions/visualstudio/visual-studio-2010/dd831853\(v\=vs.100\))|
|![Channel 9 videoları](../sharepoint/media/vs-icon-channel9videos.gif "Channel 9 videoları")|**Channel 9 videoları**<br /><br /> [Visual Studio 2010 ' de SharePoint geliştirmeye genel bakış](https://channel9.msdn.com/blogs/funkyonex/overview-of-sharepoint-development-in-visual-studio-2010) -   <br />[Visual Studio 2010 Ile SharePoint 2010 Web bölümleri derleme konusunda En Iyi yöntemleri](https://channel9.msdn.com/blogs/funkyonex/best-practices-on-building-sharepoint-2010-web-parts-with-visual-studio-2010) -   <br />[Visual Studio 2010 ' de SharePoint özellik ve paket tasarımcıları](https://channel9.msdn.com/blogs/funkyonex/sharepoint-feature-and-package-designers-in-visual-studio-2010) -   |
|![Geliştirici Merkezi](../sharepoint/media/vs-icon-msdndevcenter.gif "Geliştirici Merkezi")|**Geliştirici merkezleri**<br /><br /> -   [Visual Studio geliştirme merkezi](https://visualstudio.microsoft.com/)<br />-   [SharePoint Geliştirici Merkezi](/sharepoint/dev/)<br />-   [SharePoint Server Geliştirici Merkezi](/previous-versions/office/fp161348\(v\=office.15\))<br />-   [SharePoint Designer Geliştirici Merkezi](/previous-versions/office/fp161348\(v\=office.15\))<br />-   [ASP.NET Geliştirici Merkezi](https://msdn.microsoft.com/aa336522.aspx)|
|![Geri bildirim sağlama](../sharepoint/media/vs-icon-feedback.gif "Geri bildirim sağlama")|**Geri bildirim sağlama**<br /><br /> Visual Studio hakkında geri bildirim sağlayın:<br /><br /> -   [Microsoft Connect](/collaborate/connect-redirect)<br /><br /> Visual Studio belgeleri hakkında geri bildirim sağlayın:<br /><br /> -   **basit görünüm.** Herhangi bir konunun en üstünde yer alıyorsa, bu konunun en altına geçmek için **Bu konunun hızını** seçebilirsiniz; burada **Evet** veya **Hayır** ' ı, **Bu faydalı bulduğunuz** cevap ' i belirtebilirsiniz. Ardından **Hayır**' ı seçtiğinizde görüntülenen onay kutularından birini veya daha fazlasını seçebilir, metin kutusuna daha fazla bilgi sağlayabilir veya her ikisini birden seçebilirsiniz. Bitirdiğinizde **Gönder** düğmesini seçin.<br />**ScriptFree görünümü -   .** Konunun üst kısmında TechNet ve Expression Library geri bildirim Forumu ' nda geri bildirim sağlamak için **geri bildirim** bağlantısını seçin.<br />**Klasik görünümü -   .** Konunun üst kısmında, belge ekibine konu hakkında geri bildirim sağlamak için **derecelendirmek ve geri bildirim simgeleri vermek üzere tıklama ' yi** seçin.|
