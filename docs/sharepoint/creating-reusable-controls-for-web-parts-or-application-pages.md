---
title: Web Bölümleri Veya Application Pages | için Yeniden Kullanılabilir Denetimler Oluşturma Microsoft Docs
titleSuffix: ''
description: Uygulama sayfalarında ve web bölümleri tarafından Visual Studio özel, yeniden kullanılabilir denetimler (kullanıcı denetimleri) SharePoint.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122149513"
---
# <a name="create-reusable-controls-for-web-parts-or-application-pages"></a>Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma
  Bu Visual Studio, uygulama sayfaları tarafından tüketilen özel, yeniden kullanılabilir denetimler ve Web Bölümleri çalıştırılabilir denetimler SharePoint. Bu denetimler kullanıcı denetimleri olarak adlandırılan bir denetimdir. Kullanıcı denetimi, ASP.NET Web sayfasına çok benzer şekilde çalışan bir bileşik denetim t'tir. Bir kullanıcı denetimine mevcut Web sunucusu denetimlerini ve işaretlemesini ekleyebilir ve denetim için özellikler ve yöntemler tanımlayabilirsiniz. Daha sonra bunları bir ASP.NET gibi davranacakları web sayfalarına katıştırabilirsiniz.

## <a name="create-a-user-control"></a>Kullanıcı denetimi oluşturma
 Kullanıcı denetimi oluşturmak için Boş bir kullanıcı **denetimine** Kullanıcı **Denetimi SharePoint Project.** Daha fazla bilgi için, [bkz. How to: Create a user control for a SharePoint application page or web part](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md).

 Kullanıcı Denetimi öğesi **eklerken,** Visual Studio projeniz içinde bir klasör oluşturur ve ardından klasöre birkaç dosya ekler. Aşağıdaki tabloda her dosya açık almaktadır.

|Dosya|Açıklama|
|----------|-----------------|
|Kullanıcı denetim dosyası|Kullanıcı denetimi tanımlar. Bu dosyaya denetimler ve işaretleme ekleyerek kullanıcı denetimi tasarlar.|
|Kod dosyası|Kullanıcı denetimi arkasında kod içerir. Bu dosyaya olayları işlemek için kod ekleyin.|
|Tasarımcı kod dosyası|Tasarımcı tarafından oluşturulan kodu içerir ve doğrudan düzenlenemez.|

## <a name="design-the-user-control"></a>Kullanıcı denetimi tasarlama
 Görsel Web Geliştirici tasarımcısını kullanarak kullanıcı denetimi tasarımını Visual Studio. Bu tasarımcı, projenizin kullanıcı denetim dosyasını açıp Tasarım sekmesini seçtiğiniz **zaman** görünür.

## <a name="consume-the-user-control"></a>Kullanıcı denetimi tüketme
 Kullanıcı denetimleri bir uygulama SharePoint Web Bölümü'ne dahil inceye kadar bu denetimlerde görünmez.

 Bir uygulama sayfasına kullanıcı denetimi eklemek için, uygulama kullanıcı denetimi eklemek istediğiniz Web ASP.NET açın. Tasarım görünümü'a geçiş yapmak için özel kullanıcı denetimi dosyanızı Çözüm Gezgini seçin ve sayfaya sürükleyin. Kullanıcı ASP.NET denetimi sayfaya eklenir ve tasarımcı, sayfanın kullanıcı denetimi tanıması için gereken @ Register yönergesini oluşturur. Artık denetimin genel özellikleri ve yöntemleriyle çalışabilirsiniz.

 Bir Web Parçasına kullanıcı denetimi eklemek için, kullanıcı denetimlerini Web Bölümü <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> kod dosyasındaki Web Bölümü koleksiyonuna ekleyin. Aşağıdaki örnek, bir Web Bölümü <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> koleksiyonuna bir kullanıcı denetimi ekler.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb" id="Snippet5":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs" id="Snippet5":::

## <a name="debug-a-user-control"></a>Kullanıcı denetimi hata ayıklama
 Bir kullanıcı denetiminde hata ayıklamak için, kullanıcı denetiminizin bir uygulama sayfasına veya Web Bölümü'ne dahil olduğundan emin SharePoint edin. Daha sonra, kullanıcı denetiminde herhangi bir kaynakta kodda hata ayıklaması Visual Studio Project.

 Hata ayıklayıcısını Visual Studio, Visual Studio siteyi SharePoint açar.

 Bu SharePoint, kullanıcı denetimi içeren uygulama sayfasını açın. Kullanıcı denetimi bir Web Parçasına dahil edildiyse, Web Bölümünü bir Web Bölümü sayfasındaki SharePoint.

 Projelerde hata ayıklama hakkında daha fazla SharePoint için [bkz. SharePoint giderme.](../sharepoint/troubleshooting-sharepoint-solutions.md)

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Nasıl SharePoint uygulama sayfası veya web bölümü için kullanıcı denetimi oluşturma](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Uygulama sayfaları ve uygulama sayfalarında çalıştırılabilir özel, yeniden kullanılabilir denetimler Web Bölümleri nasıl SharePoint.|
