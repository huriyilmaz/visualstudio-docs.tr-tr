---
title: İç içe geçme projeleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 814780fa8e7e57a022a75b2e09115cfa55a1b8be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707026"
---
# <a name="nesting-projects"></a>Projeleri İç İçe Geçirme
VS Paketinizi kullanan kurumsal uygulama geliştiricileri, proje iç [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] *içe geçmeyi*kullanarak benzer proje türlerini rahatlıkla gruplaştırabilir. Örneğin, Kurumsal Şablon projesi, projeleri kategorilere gruplandırmak için iç içe yönelik projeleri kullanır. İş cephesi projeleri, Web UI projeleri ve benzeri tek bir kategoride gruplandırılır.

 Bu senaryoda, geliştirici programlı olarak sınırlar sağlayabilse de, geliştiricinin her ana proje altında yuvalayabileceği proje sayısı için bir sınır yoktur. Bu gruplandırma türü de özyinelemeli yapılabilir, bu durumda alt proje yle aynı türdeki projeler çocuğun altına iç içe çekilebilir ve bu da ebeveynin bir alt projesidir.

 Proje iç içe geçme, .'ın [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]içsel bir parçası değildir. Alt projeler içinde iç içe ve alt proje iç içe etkinleştirmek için kodu yazmanız gerekir. Ana proje, proje iç içe geçirme uygulamak için gereken kodu içeren kendi GUID'si ile oluşturulan ve kaydedilmiş özel bir VSPackage veya proje türüdür.

 İç [içe geçirilmiş projeleri](../../extensibility/internals/how-to-implement-nested-projects.md)uygulama: Projeler nasıl iç içe geçirilir hakkında bir örnek bulabilirsiniz.

## <a name="nested-projects-example"></a>İç içe projeler örneği
 ![İç Içe Projeler Çözümü](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects") İç içe projeler örneği

## <a name="see-also"></a>Ayrıca bkz.
- [İç İçe Projeleri Kaldırma ve Yeniden Yükleme Konusunda Dikkat Edilmesi Gerekenler](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [İç içe Projeler için Sihirbaz Desteği](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Proje ve Öğe Şablonlarını Kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)
- [İç içe Projeler için Komut İşlemesi Uygulama](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [İç içe Projeler için AddItem İletişim Kutusunu Filtreleme](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)
- [Denetim Listesi: Yeni Proje Türleri Oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Bağlam Parametreleri](../../extensibility/internals/context-parameters.md)
- [Sihirbaz (.Vsz) Dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)
