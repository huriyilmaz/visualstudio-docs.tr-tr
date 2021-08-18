---
title: Office geliştirme SharePoint ve Visual Studio
description: Kullanıcıların Office Store Microsoft Office'dan SharePoint basit bir uygulama veya eklenti oluşturarak uygulama ve uygulama Office nasıl genişletebilirsiniz?
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
ms.openlocfilehash: 3e377f9ea0a1f38eaedc2dd34e65b24f95acf1b3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032452"
---
# <a name="office-and-sharepoint-development-in-visual-studio"></a>Office geliştirme SharePoint ve Visual Studio
  Kullanıcıların Microsoft Office Office [Store'dan](https://store.office.com/) veya kuruluş kataloğundan indirmiş olduğu basit bir uygulama veya eklenti oluşturarak ya da kullanıcıların bir bilgisayara yüklemiş olduğu .NET Framework tabanlı bir çözüm oluşturarak .NET Framework ve SharePoint'leri genişletebilirsiniz.

 Bu konuda:

- [Office ve SharePoint](#Apps)

- [Yeni VSTO Oluşturma](#Add-ins)

- [Bir SharePoint oluşturma](#Solutions)

## <a name="create-add-ins-for-office-and-sharepoint"></a><a name="Apps"></a>Office ve SharePoint
 Office 2013 ve SharePoint 2013'te, Office ve SharePoint'yi genişleten eklentiler derlemenize, dağıtmanıza ve para kazanmanıza yardımcı olan yeni bir eklenti modeli SharePoint.  Bu eklentiler Office veya SharePoint Online'da çalışır ve kullanıcılar birçok cihazla etkileşime olabilir.

 Yeni eklenti eklenti modelini kullanarak [Office deneyimini](/office/dev/add-ins/overview/office-add-ins) genişletmek Office edinebilirsiniz.

 Bu eklentiler, VSTO ve çözümlerle karşılaştırıldığında küçük ayak izine sahiptir ve HTML5, JavaScript, CSS3 ve XML gibi neredeyse tüm web programlama teknolojisini kullanarak bunları oluşturabilirsiniz.  Çalışmaya başlamanız için Office Geliştirici Araçları proje Visual Studio kod yazmanıza ve eklentilerinizi tarayıcıda çalıştırmanıza olanak sağlayan Visual Studio'de bulunan Office Geliştirici Araçları'yi kullanın.

 ![Kavramsal model Office SharePoint uygulamalar](../vsto/media/officeandsharepointapps2015.png "Kavramsal model Office SharePoint uygulamalar")

### <a name="build-an-office-add-in"></a>Office Eklenti oluşturma
 Bir uygulamanın işlevselliğini Office için bir Office ekleyin. Bu, Office Excel, Word, Outlook ve PowerPoint gibi bir Excel uygulamasında barındırılan bir web PowerPoint. Uygulamanıza belgelere, çalışma sayfalarına, e-posta iletilerine, randevulara, sunumlara ve projelere işlevsellik ekleyebilirsiniz.

 Office Store'da Office satabilirsiniz.  Office [Store,](https://store.office.com/) eklentilerden para kazanmayı, güncelleştirmeleri yönetmeyi ve telemetri verileri izlemeyi kolaylaştırır. Ayrıca, uygulama kataloğu aracılığıyla kullanıcılara uygulama kataloğu aracılığıyla SharePoint veya Exchange Server.

 Aşağıdaki uygulama, Office çalışma sayfası verilerini bir çalışma Bing gösterir.

 ![Office için içerik uygulaması](../vsto/media/appforoffice.png "Office için içerik uygulaması")

 **Daha fazla bilgi edinin**

|Amaç|Bkz.|
|--------|---------|
|Eklenti oluşturma ve Office hakkında daha fazla bilgi edinmek için bir tane oluşturma.|[Office eklentileri](/office/dev/add-ins/publish/publish)|
|Uygulamanın süresini genişletmek için kullanabileceğiniz farklı Office uygulama mı yoksa uygulama veya uygulama Office karar verin.|[Office, VSTO ve VBA için yol haritası](/archive/blogs/officeapps/roadmap-for-apps-for-office-vsto-and-vba)|

### <a name="build-a-sharepoint-add-in"></a>SharePoint Eklenti oluşturma
 Kullanıcılarınızı SharePoint genişletmek için bir SharePoint ekleyin. Temelde kullanıcılarınıza veya işletmenize yönelik bir ihtiyacı çözen küçük, kullanımı kolay, tek başına bir uygulamadır.

 Office Store'da SharePoint [için Office satabilirsiniz.](https://store.office.com/) Eklentinizi kullanıcılara, SharePoint'daki bir eklenti kataloğu aracılığıyla da SharePoint.  Site sahipleri, bir grup sunucusu veya site koleksiyonu yöneticisinin yardımıyla SharePoint sitelerine eklentinizi yükleyebilir, yükseltebilirsiniz ve kaldırabilirsiniz.

 Kullanıcıların iş kişilerini yönetmeye yardımcı olan SharePoint için bir uygulama örneği burada ver.

 ![SharePoint için business contact manager uygulaması](../vsto/media/appforsharepoint.png "SharePoint için business contact manager uygulaması")

 **Daha fazla bilgi edinin**

|Amaç|Bkz.|
|--------|---------|
|Eklenti oluşturma ve SharePoint oluşturma hakkında daha fazla bilgi.|[SharePoint Eklentiler](/sharepoint/dev/sp-add-ins/sharepoint-add-ins)|
|SharePoint için eklentileri geleneksel SharePoint karşılaştırın.|[SharePoint Eklentiler, SharePoint çözümleriyle karşılaştırıldığında](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|
|Bir eklenti mi yoksa SharePoint çözüm mi SharePoint seçin.|[Eklenti SharePoint çözümlerini SharePoint karar verme](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|

## <a name="create-a-vsto-add-in"></a><a name="Add-ins"></a>Yeni VSTO Oluşturma
 Office 2007 veya Office 2010'a yönelik bir VSTO eklenti oluşturun ya da Office 2013 ve Office 2016'yi Office eklentileriyle mümkün olanın ötesinde genişletin. VSTO eklentileri yalnızca masaüstünde çalıştırın. Kullanıcıların ek VSTO yüklemesi gerekir, bu nedenle genellikle dağıtımı ve desteği daha zordur.  Ancak, VSTO eklentiniz, uygulamanıza daha yakın bir şekilde Office. Örneğin, Office Şerit'e sekmeler ve denetimler ekleyebilir ve belgeleri birleştirme veya grafikleri değiştirme gibi gelişmiş otomasyon görevlerini gerçekleştirebilir. Nesne nesneleriyle etkileşim .NET Framework için C# Visual Basic ve Office kullanabilirsiniz.

 Burada bir eklentinin neler VSTO bir örnek veserde yer alan bir örnek ve ardından. Bu VSTO, şerit denetimleri, özel görev bölmesi ve bir iletişim kutusu ekleyen bir PowerPoint.

 ![PowerPoint Eklenti çözümü](../vsto/media/powerpointaddin.png "PowerPoint eklenti çözümü")

 **Daha fazla bilgi edinin**

|Amaç|Okuma|
|--------|----------|
|Uygulamanın süresini genişletmenin farklı yollarını Office bir eklenti mi yoksa VSTO eklenti mi Office karar verin.|[Office, VSTO ve VBA için yol haritası](/archive/blogs/officeapps/roadmap-for-apps-for-office-vsto-and-vba)|
|Yeni VSTO oluşturun.|[VSTO eklenti derlemesi Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)|

## <a name="create-a-sharepoint-solution"></a><a name="Solutions"></a>Bir SharePoint oluşturma
 SharePoint Foundation 2010 ve SharePoint Server 2010'a yönelik bir SharePoint çözümü oluşturun veya SharePoint 2013 ve SharePoint 2016'nın bir SharePoint eklentiyle mümkün olanın ötesinde bir şekilde genişletebilirsiniz.

 SharePoint çözümleri için şirket içi ve SharePoint sunucuları gerekir. Yöneticilerin bunları yüklemesi gerekir ve çözümler SharePoint yürütülür ve sunucunun performansını etkileyebilir. Ancak çözümler, nesnelere daha derin SharePoint sağlar. Ayrıca, bir SharePoint çözümü derlemek için .NET Framework C# ve Visual Basic kullanarak SharePoint kullanabilirsiniz.

 **Daha fazla bilgi edinin**

|Amaç|Bkz.|
|--------|---------|
|Diğer SharePoint eklentilerle SharePoint karşılaştırın.|[SharePoint Eklentiler, SharePoint çözümleriyle karşılaştırıldığında](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|
|Yeni bir SharePoint oluşturun.|[Yeni SharePoint oluşturma](../sharepoint/create-sharepoint-solutions.md)|