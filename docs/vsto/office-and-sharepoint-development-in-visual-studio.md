---
title: Visual Studio Office ve SharePoint geliştirme
description: kullanıcıların Office mağazasından indirerek bir basit uygulama veya eklenti oluşturarak Microsoft Office ve SharePoint nasıl genişletebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], about developing applications
- Office development in Visual Studio
- Office projects
- Visual Studio Tools for Office, see Office development in Visual Studio
- Office applications [Office development in Visual Studio]
- Office Business Applications
- applications [Office development in Visual Studio]
- programming [Office development in Visual Studio]
- VSTO, see Office development in Visual Studio
- Office, development with Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: b22d2975404b335583acf5fa74eb261901c31bc23ced58bd349ef96058ac35f3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121331071"
---
# <a name="office-and-sharepoint-development-in-visual-studio"></a>Visual Studio Office ve SharePoint geliştirme
  kullanıcıların [Office deposundan](https://store.office.com/) veya bir kuruluş kataloğundan indirerek ya da kullanıcıların bir bilgisayara yükleyen .NET Framework tabanlı bir çözüm oluşturarak Microsoft Office ve SharePoint genişletebilirsiniz.

 Bu konuda:

- [Office ve SharePoint için eklentiler oluşturma](#Apps)

- [VSTO eklentisi oluşturma](#Add-ins)

- [SharePoint çözümü oluşturma](#Solutions)

## <a name="create-add-ins-for-office-and-sharepoint"></a><a name="Apps"></a>Office ve SharePoint için eklentiler oluşturma
 Office 2013 ve SharePoint 2013, Office ve SharePoint genişleten eklentiler oluşturmanıza, dağıtmanıza ve bunları yeniden oluşturmanıza yardımcı olan yeni bir eklenti modeli sunuyor.  bu eklentiler Office veya çevrimiçi SharePoint çalışabilir ve kullanıcılar birçok cihazdan bunlarla etkileşime girebilirler.

 yeni [Office eklentisi modelinin](/office/dev/add-ins/overview/office-add-ins) , kullanıcılarınız için Office deneyimini uzatmak üzere nasıl kullanılacağını öğrenin.

 bu eklentiler, VSTO eklentileri ve çözümleri ile karşılaştırıldığında küçük bir baskı ve HTML5, JavaScript, CSS3 ve XML gibi neredeyse her türlü web programlama teknolojisini kullanarak da oluşturabilirsiniz.  başlamak için, Visual Studio Office Geliştirici Araçları kullanın. bu, proje oluşturmanızı, kod yazmanızı ve eklentilerinizi bir tarayıcıda çalıştırmanızı sağlar.

 ![Office ve SharePoint kavramsal model için uygulamalar](../vsto/media/officeandsharepointapps2015.png "Office ve SharePoint kavramsal model için uygulamalar")

### <a name="build-an-office-add-in"></a>Office eklentisi oluşturma
 Office işlevlerini genişletmek için bir Office eklentisi oluşturun. bu, temel olarak Excel, Word, Outlook ve PowerPoint gibi Office bir uygulamada barındırılan bir web sayfasıdır. Uygulamanız belgelere, çalışma sayfalarına, e-posta iletilerine, randevulara, sunulara ve projelere işlevsellik ekleyebilir.

 uygulamanızı Office deposuna satabilirsiniz.  [Office deposu](https://store.office.com/) , eklentilerinizi izlemeyi, güncelleştirmeleri yönetmenizi ve telemetriyi izlemenizi kolaylaştırır. ayrıca, SharePoint veya Exchange Server bir uygulama kataloğu aracılığıyla uygulamanızı kullanıcılara yayımlayabilirsiniz.

 Office için aşağıdaki uygulama, Bing eşlemesindeki çalışma sayfası verilerini gösterir.

 ![Office için içerik uygulaması](../vsto/media/appforoffice.png "Office için içerik uygulaması")

 **Daha fazla bilgi edinin**

|Amaç|Bkz.|
|--------|---------|
|Office eklentileri hakkında daha fazla bilgi edinin ve ardından bir tane oluşturun.|[Office eklentiler](/office/dev/add-ins/publish/publish)|
|Office genişletebileceğiniz farklı yolları karşılaştırın ve bir uygulama mı yoksa Office eklentisi mi kullanacağınızı belirleyin.|[Office eklentileri, VSTO ve VBA için yol haritası](/archive/blogs/officeapps/roadmap-for-apps-for-office-vsto-and-vba)|

### <a name="build-a-sharepoint-add-in"></a>SharePoint eklentisi oluşturma
 kullanıcılarınız için SharePoint genişletmek için bir SharePoint eklentisi oluşturun. Bu temelde, kullanıcılarınız veya işletmeniz için ihtiyacı çözen küçük, kullanımı kolay, tek başına bir uygulamadır.

 uygulamanızı [Office mağazasındaki](https://store.office.com/)SharePoint satıtabilirsiniz. Ayrıca, SharePoint bir eklenti Kataloğu aracılığıyla kullanıcılarınıza eklenti yayımlayabilirsiniz.  site sahipleri, bir grup sunucusunun veya site koleksiyonu yöneticisinin yardımı olmadan, SharePoint sitelerine eklentiyi yükleyebilir, yükseltebilir ve kaldırabilir.

 kullanıcıların iş kişilerini yönetmesine yardımcı olan SharePoint bir uygulama örneği aşağıda verilmiştir.

 ![SharePoint için Business Contact Manager uygulaması](../vsto/media/appforsharepoint.png "SharePoint için Business Contact Manager uygulaması")

 **Daha fazla bilgi edinin**

|Amaç|Bkz.|
|--------|---------|
|SharePoint eklentileri hakkında daha fazla bilgi edinin ve ardından bir tane oluşturun.|[SharePoint Eklentiler](/sharepoint/dev/sp-add-ins/sharepoint-add-ins)|
|eklentileri geleneksel SharePoint çözümleriyle SharePoint karşılaştırın.|[SharePoint SharePoint çözümleriyle karşılaştırılan eklentiler](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|
|SharePoint eklenti veya SharePoint çözümü oluşturulup oluşturulmayacağını seçin.|[SharePoint eklentileri ve SharePoint çözümleri arasında karar verme](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|

## <a name="create-a-vsto-add-in"></a><a name="Add-ins"></a>VSTO eklentisi oluşturma
 Office 2007 veya Office 2010 ' i hedeflemek ya da Office 2013 ' ı uzatmak için VSTO bir eklenti oluşturun veya Office eklentileriyle mümkün olan işlemleri ötesinde Office 2016. VSTO eklentiler yalnızca masaüstünde çalışır. kullanıcıların VSTO eklentileri yüklemeleri gerekir, bu yüzden genellikle dağıtımı ve desteği daha zordur.  ancak, VSTO eklentisi Office daha yakından tümleştirilebilir. örneğin, Office şeridine sekmeler ve denetimler ekleyebilir ve belge birleştirme ya da grafikleri değiştirme gibi gelişmiş otomasyon görevlerini gerçekleştirebilir. .NET Framework yararlanabilir ve Office nesneleriyle etkileşimde bulunmak için C# ve Visual Basic kullanabilirsiniz.

 işte VSTO eklentisinin yapabilecekleri bir örnek. bu VSTO eklenti, PowerPoint için şerit denetimleri, özel görev bölmesi ve iletişim kutusu ekler.

 ![PowerPoint Eklenti çözümü](../vsto/media/powerpointaddin.png "PowerPoint eklentisi çözümü")

 **Daha fazla bilgi edinin**

|Amaç|Okuma|
|--------|----------|
|Office genişletebileceğiniz farklı yolları karşılaştırın ve bir VSTO eklentisi mi yoksa Office eklentisi mi kullanacağınızı belirleyin.|[Office eklentileri, VSTO ve VBA için yol haritası](/archive/blogs/officeapps/roadmap-for-apps-for-office-vsto-and-vba)|
|VSTO eklentisi oluşturun.|[Visual Studio VSTO eklentileri oluşturma](create-vsto-add-ins-for-office-by-using-visual-studio.md)|

## <a name="create-a-sharepoint-solution"></a><a name="Solutions"></a>SharePoint çözümü oluşturma
 SharePoint Foundation 2010 ve SharePoint Server 2010 ' i hedeflemek veya SharePoint 2013 ve SharePoint 2016 ' i SharePoint bir eklenti ile mümkün olduğunca fazla şekilde genişletmek için SharePoint bir çözüm oluşturun.

 SharePoint çözümleri şirket içi SharePoint grubu sunucuları gerektirir. yöneticiler bu yüklemeleri yüklemelidir ve çözümler SharePoint içinde yürütülecektir, sunucunun performansını etkileyebilir. ancak, çözümler SharePoint nesnelerine daha derin erişim sağlar. ayrıca, bir SharePoint çözümü oluşturduğunuzda .NET Framework ve C# ve Visual Basic kullanarak SharePoint nesneleriyle etkileşim kurabilirsiniz.

 **Daha fazla bilgi edinin**

|Amaç|Bkz.|
|--------|---------|
|SharePoint çözümlerini SharePoint eklentileriyle karşılaştırın.|[SharePoint SharePoint çözümleriyle karşılaştırılan eklentiler](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|
|SharePoint çözümü oluşturun.|[SharePoint çözümleri oluşturma](../sharepoint/create-sharepoint-solutions.md)|