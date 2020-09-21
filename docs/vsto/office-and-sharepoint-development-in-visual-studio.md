---
title: Visual Studio 'da Office ve SharePoint geliştirme
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bc1241a39707eedc4b34e0ef3531ab65e49b8238
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90811038"
---
# <a name="office-and-sharepoint-development-in-visual-studio"></a>Visual Studio 'da Office ve SharePoint geliştirme
  Kullanıcıların [Office mağazasından](https://store.office.com/) veya bir kuruluş kataloğundan indirerek bir basit uygulama ya da eklenti oluşturarak ya da kullanıcıların bir bilgisayara yükleyen .NET Framework tabanlı bir çözüm oluşturarak Microsoft Office ve SharePoint 'i genişletebilirsiniz.

 Bu konuda:

- [Office ve SharePoint için eklentiler oluşturma](#Apps)

- [VSTO eklentisi oluşturma](#Add-ins)

- [SharePoint çözümü oluşturma](#Solutions)

## <a name="create-add-ins-for-office-and-sharepoint"></a><a name="Apps"></a> Office ve SharePoint için eklentiler oluşturma
 Office 2013 ve SharePoint 2013, Office ve SharePoint 'i genişleten eklentiler oluşturmanıza, dağıtmanıza ve bunları yeniden almanıza yardımcı olan yeni bir eklenti modeli sunar.  Bu eklentiler Office veya SharePoint Online 'da çalışabilir ve kullanıcılar birçok cihazdan bunlarla etkileşime girebilirler.

 Yeni [Office eklentisi modelinin](/office/dev/add-ins/overview/office-add-ins) , kullanıcılarınız için Office deneyimini uzatmak üzere nasıl kullanılacağını öğrenin.

 Bu eklentilerin, VSTO eklentileri ve çözümleri ile karşılaştırıldığında küçük bir baskı ve HTML5, JavaScript, CSS3 ve XML gibi neredeyse her türlü Web programlama teknolojisini kullanarak bunları oluşturabilirsiniz.  Başlamak için, Visual Studio 'daki Office Geliştirici Araçları kullanın. Bu, proje oluşturmanızı, kod yazmanızı ve Eklentilerinizi bir tarayıcıda çalıştırmanızı sağlar.

 ![Office ve SharePoint için uygulamalar kavramsal modeli](../vsto/media/officeandsharepointapps2015.png "Office ve SharePoint için uygulamalar kavramsal modeli")

### <a name="build-an-office-add-in"></a>Office eklentisi oluşturma
 Office işlevlerini genişletmek için bir Office eklentisi oluşturun. Bu, aslında Excel, Word, Outlook ve PowerPoint gibi bir Office uygulamasında barındırılan bir Web sayfasıdır. Uygulamanız belgelere, çalışma sayfalarına, e-posta iletilerine, randevulara, sunulara ve projelere işlevsellik ekleyebilir.

 Uygulamanızı Office Mağazası 'nda satın alabilirsiniz.  [Office Mağazası](https://store.office.com/) , eklentilerinizi izlemeyi, güncelleştirmeleri yönetmenizi ve Telemetriyi izlemenizi kolaylaştırır. Ayrıca, uygulamanızı SharePoint 'te veya Exchange Server 'da Uygulama Kataloğu aracılığıyla kullanıcılara yayımlayabilirsiniz.

 Office için aşağıdaki uygulama, bir Bing eşlemesindeki çalışma sayfası verilerini gösterir.

 ![Office için içerik uygulaması](../vsto/media/appforoffice.png "Office için içerik uygulaması")

 **Daha fazla bilgi edinin**

|Amaç|Bkz.|
|--------|---------|
|Office eklentileri hakkında daha fazla bilgi edinin ve ardından bir tane oluşturun.|[Office eklentileri](/office/dev/add-ins/publish/publish)|
|Office 'i genişletebileceğiniz farklı yolları karşılaştırın ve bir uygulama mı yoksa Office eklentisi mi kullanacağınızı belirleyin.|[Office eklentileri, VSTO ve VBA için yol haritası](/archive/blogs/officeapps/roadmap-for-apps-for-office-vsto-and-vba)|

### <a name="build-a-sharepoint-add-in"></a>SharePoint eklentisi oluşturma
 Kullanıcılarınıza yönelik SharePoint 'i genişletmek için bir SharePoint eklentisi oluşturun. Bu temelde, kullanıcılarınız veya işletmeniz için ihtiyacı çözen küçük, kullanımı kolay, tek başına bir uygulamadır.

 SharePoint için uygulamanızı [Office Mağazası](https://store.office.com/)'nda satıtabilirsiniz. Ayrıca eklentisini, SharePoint 'teki bir eklenti Kataloğu aracılığıyla kullanıcılara yayımlayabilirsiniz.  Site sahipleri, bir grup sunucusunun veya site koleksiyonu yöneticisinin yardımı olmadan eklentilerinizi SharePoint sitelerinde yükleyebilir, yükseltebilir ve kaldırabilir.

 Kullanıcıların iş kişilerini yönetmesine yardımcı olan bir SharePoint uygulamasına bir örnek aşağıda verilmiştir.

 ![SharePoint için Business Contact Manager uygulaması](../vsto/media/appforsharepoint.png "SharePoint için Business Contact Manager uygulaması")

 **Daha fazla bilgi edinin**

|Amaç|Bkz.|
|--------|---------|
|SharePoint eklentileri hakkında daha fazla bilgi edinin ve ardından bir tane oluşturun.|[SharePoint eklentileri](/sharepoint/dev/sp-add-ins/sharepoint-add-ins)|
|SharePoint için eklentileri geleneksel SharePoint çözümleriyle karşılaştırın.|[SharePoint çözümleri ile karşılaştırıldığında SharePoint eklentileri](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|
|SharePoint eklentisi veya SharePoint çözümünün oluşturulup oluşturulmayacağını seçin.|[SharePoint eklentileri ve SharePoint çözümleri arasında karar verme](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|

## <a name="create-a-vsto-add-in"></a><a name="Add-ins"></a> VSTO eklentisi oluşturma
 Office 2007 veya Office 2010 ' i hedeflemek veya Office 2013 ve Office 2016 ' i Office eklentileriyle mümkün olduğunca fazla genişletmek için bir VSTO eklentisi oluşturun. VSTO eklentileri yalnızca masaüstünde çalışır. Kullanıcıların VSTO Eklentilerini yüklemeleri gerekir, bu yüzden genellikle dağıtımı ve desteği daha zordur.  Ancak, VSTO eklentisi Office ile daha yakından tümleştirilebilir. Örneğin, Office şeridine sekmeler ve denetimler ekleyebilir ve belge birleştirme ya da grafikleri değiştirme gibi gelişmiş otomasyon görevleri gerçekleştirebilirsiniz. Office nesneleriyle etkileşim kurmak için .NET Framework yararlanabilir ve C# ve Visual Basic kullanabilirsiniz.

 VSTO eklentisinin neler yapabileceğini bir örnek aşağıda bulabilirsiniz. Bu VSTO eklentisi, Şerit denetimleri, özel bir görev bölmesi ve bir iletişim kutusunu PowerPoint 'e ekler.

 ![PowerPoint eklentisi çözümü](../vsto/media/powerpointaddin.png "PowerPoint eklentisi çözümü")

 **Daha fazla bilgi edinin**

|Amaç|Okuma|
|--------|----------|
|Office 'i genişletebileceğiniz farklı yolları karşılaştırın ve bir VSTO eklentisi mi yoksa Office eklentisi mi kullanacağınızı belirleyin.|[Office eklentileri, VSTO ve VBA için yol haritası](/archive/blogs/officeapps/roadmap-for-apps-for-office-vsto-and-vba)|
|VSTO eklentisi oluşturun.|[Visual Studio ile VSTO eklentileri oluşturma](create-vsto-add-ins-for-office-by-using-visual-studio.md)|

## <a name="create-a-sharepoint-solution"></a><a name="Solutions"></a> SharePoint çözümü oluşturma
 SharePoint Foundation 2010 ve SharePoint Server 2010 ' i hedeflemek için bir SharePoint çözümü oluşturun veya SharePoint eklentisi ile mümkün olduğunca fazla şekilde SharePoint 2013 ve SharePoint 2016 ' i genişletin.

 SharePoint çözümleri, şirket içi SharePoint grubu sunucuları gerektirir. Yöneticiler bu yüklemeleri yüklemelidir ve SharePoint 'te çözümler yürütültiğinden, sunucunun performansını etkileyebilirler. Ancak, çözümler SharePoint nesnelerine daha derin erişim sağlar. Ayrıca, bir SharePoint çözümü oluşturduğunuzda .NET Framework kullanabilir ve C# ve Visual Basic kullanarak SharePoint nesneleriyle etkileşim kurabilirsiniz.

 **Daha fazla bilgi edinin**

|Amaç|Bkz.|
|--------|---------|
|SharePoint çözümlerini SharePoint eklentileriyle karşılaştırın.|[SharePoint çözümleri ile karşılaştırıldığında SharePoint eklentileri](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|
|Bir SharePoint çözümü oluşturun.|[SharePoint çözümleri oluşturma](../sharepoint/create-sharepoint-solutions.md)|