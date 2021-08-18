---
title: SharePoint Solutions | Microsoft Docs
description: Uygulama uygulamalarının Visual Studio yardımcı olmak için hangi özelliklerin SharePoint keşfedin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- security [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, security
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: d287552b07f67c7415688fefd87f876242b230f4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084070"
---
# <a name="security-for-sharepoint-solutions"></a>SharePoint çözümleri için güvenlik
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]uygulamaların güvenliğini artırmaya yardımcı olmak için aşağıdaki SharePoint içerir.

## <a name="safe-control-entries"></a>Kasa girişlerini denetleme
 içinde SharePoint her proje [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] öğesi, güvenli **denetim Kasa temsil** eden bir Denetim Girdileri özelliğine sahiptir. Bu **Kasa** özelliği, güvenli olarak değerlendirilen denetimleri belirtmenize olanak sağlar. Daha fazla bilgi için [bkz. Proje öğelerinde paket ve dağıtım bilgilerini sağlama ve](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) [Kasa Web Bölümleri.](/previous-versions/office/developer/sharepoint2003/dd583154(v=office.11)#specifying-safe-web-parts)

## <a name="allowpartiallytrustedcallers-attribute"></a>AllowPartiallyTrustedCallers özniteliği
 Varsayılan olarak, yalnızca çalışma zamanı kod erişim güvenliği (CAS) sistemi tarafından tam olarak güvenilen uygulamalar paylaşılan yönetilen kod derlemelerine erişebilirsiniz. AllowPartiallyTrustedCallers özniteliğiyle tam olarak güvenilen bir derlemeyi işaretlemek, kısmen güvenilen derlemelerin bu derlemeye erişmesine olanak sağlar.

 AllowPartiallyTrustedCallers özniteliği, sistem genel derleme önbelleğine SharePoint herhangi bir çözüme eklenir ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)] ). Bu, SharePoint uygulama Bin dizinine dağıtılan korumalı SharePoint çözümleri içerir. Daha fazla bilgi için bkz. Microsoft .NET Framework için Sürüm [1](/previous-versions/msp-n-p/ff921345(v=pandp.10)) Güvenlik Değişiklikleri ve [Web Bölümleri SharePoint Foundation.](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14))

## <a name="safe-against-script-property"></a>Kasa betik özelliğine karşı güvenlik
 *Betik ekleme,* kötü amaçlı olabilecek kodun denetimlere veya Web sayfalarına yerleştirilmesidir. 2010 SharePoint betik eklemeye karşı korumaya yardımcı olmak için katkıda bulunanlar Web bölümlerini veya özelliklerini varsayılan olarak görüntüleyemez veya düzenleyemez. Bu davranış SafeAgainstScript adlı bir SafeControl özniteliği tarafından denetlenmektedir. içinde, bu özniteliği bir proje öğesinin Komut Kasa Denetimi Girdileri [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] altöz **Kasa için ayarlayın.**  Daha fazla bilgi için [bkz. Proje öğelerinde paket ve](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) dağıtım bilgilerini sağlama ve [Nasıl kullanılır: Denetimleri güvenli denetimler olarak işaretleme.](../sharepoint/how-to-mark-controls-as-safe-controls.md)

## <a name="vista-and-windows-7-user-account-control"></a>Vista ve Windows 7 Kullanıcı Hesabı Denetimi
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] ve [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] Kullanıcı Hesabı Denetimi (UAC) olarak bilinen bir güvenlik özelliğine sahiptir. ve sistemlerinde SharePoint çözümleri [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] geliştirmek [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] için UAC, sistem yöneticisi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] olarak çalıştırmanız gerekir. Başlat **menüsünden** kısayol menüsünü açın ve Ardından [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Yönetici olarak **çalıştır'ı seçin.**

 Kısayolu her zaman yönetici olarak çalıştıracak şekilde yapılandırmak için kısayol menüsünü açın, Özellikler'i seçin, Özellikler iletişim kutusunda Gelişmiş düğmesini seçin ve ardından Yönetici olarak çalıştır [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **onay** kutusunu seçin.   

 Daha fazla bilgi için, [bkz. Understanding and Configuring User Account Control in Windows Vista](/previous-versions/windows/it-pro/windows-vista/cc709628(v=ws.10)). ve [Windows 7 Kullanıcı Hesabı Denetimi.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731416(v=ws.10))

## <a name="sharepoint-permissions-considerations"></a>SharePoint izinler hakkında dikkat edilmesi gerekenler
 Bu SharePoint geliştirmek için, bu çözümleri çalıştırmak ve hata ayıklamak için yeterli izinlere SharePoint gerekir. Bir çözümde test SharePoint önce, gerekli izinlere sahip olduğundan emin olmak için aşağıdaki adımları uygulayın:

1. Kullanıcı hesabını sistemde Yönetici olarak ekleyin.

2. SharePoint sunucusu için kullanıcı hesabını Grup Yöneticisi SharePoint ekleyin.

    1. 2010 SharePoint Yönetim'de Grup yöneticilerini **yönet grup bağlantısını** seçin.

    2. Grup **Yöneticileri sayfasında** Yeni menü **seçeneğini** belirleyin

3. Kullanıcı hesabınıza kullanıcı WSS_ADMIN_WPG ekleyin.

## <a name="additional-security-resources"></a>Ek güvenlik seçenekleri
 Güvenlik sorunları hakkında daha fazla bilgi için aşağıdakilere bakın.

### <a name="visual-studio-security"></a>Visual Studio güvenliği

- [Güvenlik ve Kullanıcı İzinleri](/previous-versions/visualstudio/visual-studio-2010/ms165099(v=vs.100))

- [Yerel kodda ve .NET Framework güvenlik](/previous-versions/visualstudio/visual-studio-2010/1787tk12(v=vs.100))

- [.NET Framework'te Güvenlik](/previous-versions/dotnet/netframework-4.0/fkytk30f(v=vs.100))

### <a name="sharepoint-security"></a>SharePoint güvenlik

- [SharePoint Temel Yönetim ve Güvenlik](/previous-versions/office/developer/sharepoint-2010/ee537811(v=office.14))

- [SharePoint Güvenlik Kaynak Merkezi](/sharepoint/dev/)

- [SharePoint Foundation Web Bölümleri da Web Bölümleri güvenliğini sağlama](/previous-versions/office/developer/sharepoint-2010/cc768613(v=office.14))

- [Web Uygulaması Güvenliğini Geliştirme: Tehditler ve Karşı önlemler](/previous-versions/msp-n-p/ff649874(v=pandp.10))

### <a name="general-security"></a>Genel güvenlik

- [MSDN Güvenlik Geliştirme Yaşam Döngüsü](https://www.microsoft.com/msrc?rtc=1)

- [Güvenli ASP.NET Uygulamaları: Kimlik Doğrulaması, Yetkilendirme ve Güvenli İletişim](/previous-versions/msp-n-p/ff649100(v=pandp.10))

## <a name="see-also"></a>Ayrıca bkz.

- [Yeni SharePoint geliştirme](../sharepoint/developing-sharepoint-solutions.md)