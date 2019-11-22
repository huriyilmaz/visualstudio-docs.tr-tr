---
title: Visual Studio yaşam döngüsü Ilkesi özel durumları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
ms.assetid: c238489d-6181-42c6-aa60-f75d0889dc68
caps.latest.revision: 3
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 6db11d583818f1ea63c490cd8f588cb005b50a8d
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295935"
---
# <a name="visual-studio-lifecycle-policy-exceptions"></a>Visual Studio Yaşam Döngüsü İlkesine Yönelik Özel Durumlar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio, derleyiciler, diller, çalışma zamanları, ortamlar ve diğer kaynaklardan oluşturulmuş, birçok Microsoft platformu için geliştirmeye olanak tanıyan bir koleksiyon içerir. Visual Studio müşterilerimize kolaylık sağlamak için, Visual Studio söz konusu Microsoft platformlarını hedefleyen ve destekleyen bazı Microsoft SDK’lerini ve diğer Microsoft bileşenlerini yükleyebilir. Bu bileşenler, kendi koşulları ve ilkeleri kapsamında lisanslandır ve desteklenir.  
  
## <a name="external-components-that-follow-a-lifecycle-policy-other-than-the-visual-studio-policy"></a>Visual Studio ilkesi dışında bir yaşam döngüsü ilkesini izleyen dış bileşenler  
 Aşağıdaki tabloda, Visual Studio 'ya dahil olabilen Microsoft platform bileşenleri (Visual Studio yazılımının belirli sürümüne bağlı olarak) listelenmekte ve bunlar kendi destek ilkelerine ve zaman çerçevelerine tabidir.  
  
|ÜRÜN AILESI|DıŞ AD|  
|--------------------|-------------------|  
|[.NET 3,5](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=net%20framework%203.5&Filter=FilterNO)|.NET 3.5 SDK<br /><br /> Windows Identity Foundation|  
|[.NET 4,5](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=net%20framework%204.5&Filter=FilterNO)|.NET 4.5 SDK|  
|[.NET 4.5.1](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=.NET%20Framework%204.5.1&Filter=FilterNO)|.NET 4.5.1 MT Pack (Klasik)<br /><br /> .NET 4.5.1 Çoklu Sürüm Desteği Paketi (Mağaza)<br /><br /> .NET 4.5.1 OOB MSU<br /><br /> .NET 4.5.1 Redist<br /><br /> .NET 4.5.1 Yeniden Dağıtılabilir Dil Paketleri<br /><br /> .NET 4.5.1 SDK|  
|[ASP.NET Web Yığını](https://go.microsoft.com/fwlink/?LinkId=328918)|ASP.NET MVC 4<br /><br /> ASP.NET MVC 5<br /><br /> ASP.NET Web API<br /><br /> ASP.NET Web API 2<br /><br /> ASP.NET Web Sayfaları 2<br /><br /> ASP.NET Web Sayfaları 3|  
|[Entity Framework 6](https://go.microsoft.com/fwlink/?LinkId=328950)|Entity Framework 6|  
|[Exchange 2013](https://go.microsoft.com/fwlink/?LinkId=328950)|Exchange Web Hizmetleri|  
|[Microsoft OWIN](https://go.microsoft.com/fwlink/?LinkId=328951)|Microsoft OWIN|  
|[Microsoft Web Geliştirici Araçları 2013](https://go.microsoft.com/fwlink/?LinkId=328952)|Microsoft Web Geliştirici Araçları 2013|  
|Bu bileşenlerde yapılan güncelleştirmeler NuGet üzerinden dağıtılır ve standart Microsoft yaşam döngüsü ilkelerine uymaz.  Daha fazla bilgi için bkz. [http://docs.nuget.org/](https://docs.microsoft.com/nuget/) .|Microsoft .NET Framework 4,5 için JSON Web Token Işleyicisi<br /><br /> NuGet 2.7<br /><br /> SignalR<br /><br /> Web Optimization Framework<br /><br /> WebGrease|  
|[ODataLib](https://go.microsoft.com/fwlink/?LinkId=328954)|ODataLib|  
|[Office 2013](https://support.microsoft.com/lifecycle/search/?p1=16674)|Open XML SDK|  
|[Çevrimiçi hizmetler Ilkesi](https://support.microsoft.com/hub/4095338/microsoft-lifecycle-policy)|Microsoft Ads SDK|  
|[SharePoint 2013](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=sharepoint%20server%202013&Filter=FilterNO)|SharePoint İstemci Bileşenleri<br /><br /> SharePoint Foundation 2013<br /><br /> Windows Identity Foundation Uzantıları|  
|[Silverlight 5](https://support.microsoft.com/lifecycle/search/?p1=16278)<br /><br /> <br />> Ayrıca bkz: [http://support.microsoft.com/gp/lifean45](https://support.microsoft.com/gp/lifean45)|Silverlight 5 Çalışma Zamanı<br /><br /> Silverlight 5 SDK|  
|[SQL Server 2008 R2](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=SQL%20Server%202008%20R2&Filter=FilterNO)|SQL Sistem CLR Türleri (SQL Server 2008 R2)|  
|[SQL Server 2012](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=SQL%20Server%202012&Filter=FilterNO)|DACFx (DACFramework)<br /><br /> SMO (SharedManagementObjects)<br /><br /> SQL Komut Satırı Yardımcı Programları<br /><br /> SQL dil hizmeti-IntelliSense (TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> SQL Yerel İstemcisi (Sqlncli)<br /><br /> SQL Server Express 2012 SP1<br /><br /> SQL Sistemi CLR Türleri (SQL Server 2012)<br /><br /> SQLDOM|  
|[SQL Server 2014](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=SQL%20Server%202014&Filter=FilterNO)|DACFx (DACFramework)<br /><br /> SMO (SharedManagementObjects)<br /><br /> SQL Komut Satırı Yardımcı Programları<br /><br /> SQL dil hizmeti-IntelliSense (TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> SQL Yerel İstemcisi (Sqlncli)<br /><br /> SQL Server Express 2014<br /><br /> SQL Sistem CLR Türleri (SQL Server 2014)<br /><br /> SQLDOM|  
|[SQL Server Compact Edition 4,0](https://support.microsoft.com/lifecycle/search/?p1=16106)|SQL Server Compact Edition 4.0|  
|[WCF RıA Hizmetleri v 1.0 SP2](https://go.microsoft.com/fwlink/?LinkId=328955)|WCF RIA Services v1.0 SP2|  
|[Windows Server 2008](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=Windows%20Server%202008&Filter=FilterNO)|Windows Server 2008 için Windows Web Hizmetleri (WWS)|  
|[Windows 7](https://support.microsoft.com/lifecycle/search/?c2=14019)|Windows 7 SDK|  
|[Windows 8](https://support.microsoft.com/lifecycle/search/?c2=16796)|Windows 8 SDK|  
|[Windows 8.1](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=windows%208.1&Filter=FilterNO)|Windows 8.1 SDK<br /><br /> JavaScript için Windows Kitaplığı (WinJS)|  
|[Microsoft Azure](https://support.microsoft.com/help/18486/lifecycle-faq-azure)<br /><br /> <br />> Ayrıca bkz: [çevrimiçi yaşam döngüsü ilkesi](https://support.microsoft.com/hub/4095338/microsoft-lifecycle-policy)|Microsoft Azure Mobile Services SDK<br /><br /> Microsoft Azure Mobile Services Araçları|