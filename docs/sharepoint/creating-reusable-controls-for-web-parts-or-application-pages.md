---
title: Web Bölümleri veya Application Pages | için Yeniden Kullanılabilir Denetimler Oluşturma Microsoft Docs
titleSuffix: ''
description: Uygulama sayfaları ve web bölümleri tarafından Visual Studio için özel, yeniden kullanılabilir denetimler (kullanıcı denetimleri) SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- SharePoint development in Visual Studio, user controls
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: a60b33e73991a1ce5ec75937e07d3f108b6abf61
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635657"
---
# <a name="create-reusable-controls-for-web-parts-or-application-pages"></a>Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma
  Bu Visual Studio, uygulama sayfaları tarafından tüketilen özel, yeniden kullanılabilir denetimler ve Web Bölümleri çalıştırılabilir denetimler SharePoint. Bu denetimler kullanıcı denetimleri olarak adlandırılan bir denetimdir. Kullanıcı denetimi, ASP.NET Web sayfasına çok benzer şekilde çalışan bir bileşik denetim t'tir. Bir kullanıcı denetimine mevcut Web sunucusu denetimlerini ve işaretlemesini ekleyebilir ve denetim için özellikler ve yöntemler tanımlayabilirsiniz. Daha sonra bunları bir ASP.NET gibi davranacakları web sayfalarına katıştırabilirsiniz.

## <a name="create-a-user-control"></a>Kullanıcı denetimi oluşturma
 Kullanıcı denetimi oluşturmak için Boş bir kullanıcı **denetimine** Kullanıcı Denetimi **SharePoint Project.** Daha fazla bilgi için bkz. Nasıl 2. Bir uygulama sayfası [SharePoint web bölümü için kullanıcı denetimi oluşturma.](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)

 Kullanıcı Denetimi öğesi **eklerken,** Visual Studio projeniz içinde bir klasör oluşturur ve ardından klasöre birkaç dosya ekler. Aşağıdaki tabloda her dosya açık almaktadır.

|Dosya|Description|
|----------|-----------------|
|Kullanıcı denetim dosyası|Kullanıcı denetimi tanımlar. Bu dosyaya denetimler ve işaretleme ekleyerek kullanıcı denetimi tasarlar.|
|Kod dosyası|Kullanıcı denetimi arkasında kod içerir. Bu dosyaya olayları işlemek için kod ekleyin.|
|Tasarımcı kod dosyası|Tasarımcı tarafından oluşturulan kodu içerir ve doğrudan düzenlenemez.|

## <a name="design-the-user-control"></a>Kullanıcı denetimi tasarlama
 Web'de Visual Web Geliştirici tasarımcısını kullanarak kullanıcı Visual Studio. Bu tasarımcı, projenizin kullanıcı denetim dosyasını açıp Tasarım sekmesini seçtiğiniz **zaman** görünür.

## <a name="consume-the-user-control"></a>Kullanıcı denetimi tüketme
 Kullanıcı denetimleri bir uygulama SharePoint Web Bölümü'ne dahil inceye kadar bu denetimlerde görünmez.

 Uygulama sayfasına kullanıcı denetimi eklemek için, uygulama kullanıcı denetimine kullanıcı denetimi eklemek ASP.NET açın. Yeni Tasarım görünümü, ardından dosyanın içinde özel kullanıcı denetimi Çözüm Gezgini seçin ve sayfaya sürükleyin. Kullanıcı ASP.NET denetimi sayfaya eklenir ve tasarımcı, sayfanın kullanıcı denetimi tanıması için gereken @ Register yönergesini oluşturur. Artık denetimin genel özellikleri ve yöntemleriyle çalışabilirsiniz.

 Bir Web Parçasına kullanıcı denetimi eklemek için, web bölümü kod dosyasındaki Web Bölümü <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> koleksiyonuna kullanıcı denetimi ekleyin. Aşağıdaki örnek, bir Web Bölümü <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> koleksiyonuna bir kullanıcı denetimi ekler.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb" id="Snippet5":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs" id="Snippet5":::

## <a name="debug-a-user-control"></a>Kullanıcı denetimi hata ayıklama
 Bir kullanıcı denetiminde hata ayıklamak için, kullanıcı denetiminizin bir uygulama sayfasına veya Web Bölümü'ne dahil olduğundan emin SharePoint edin. Daha sonra, kullanıcı denetiminde herhangi bir kaynakta kodda hata ayıklaması Visual Studio Project.

 Hata ayıklayıcısını Visual Studio, Visual Studio siteyi SharePoint açar.

 Bu SharePoint, kullanıcı denetimi içeren uygulama sayfasını açın. Kullanıcı denetimi bir Web Parçasına dahil edildiyse, Web Bölümünü web sayfasındaki bir Web SharePoint.

 Projelerde hata ayıklama hakkında daha fazla SharePoint için [bkz. SharePoint giderme.](../sharepoint/troubleshooting-sharepoint-solutions.md)

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Nasıl SharePoint uygulama sayfası veya web bölümü için kullanıcı denetimi oluşturma](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Uygulama sayfaları ve uygulama sayfalarında çalıştırılabilir özel, yeniden kullanılabilir denetimler Web Bölümleri nasıl SharePoint.|
