---
title: Projeleri iç içe geçirme | Microsoft Docs
description: VSPackage 'ı kullanan uygulama geliştiricilerinin, Visual Studio 'da benzer türdeki projeleri gruplamak için, iç içe geçme projeleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 464538d7f7be68737715cb6fd10fda4017a5556a
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876668"
---
# <a name="nesting-projects"></a>Projeleri İç İçe Geçirme
VS paketinizi kullanan kurumsal uygulama geliştiricileri, içindeki [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] *proje iç içe geçme* kullanarak benzer proje türlerini kolayca gruplandırabilir. Örneğin, kurumsal şablon proje, projeleri kategoriler halinde gruplamak için iç içe geçmiş projeleri kullanır. İş façlade projeleri, Web UI projeleri vb. bir kategoride birlikte gruplandırılır.

 Bu senaryoda, geliştirici program aracılığıyla sınırları sağlayabilse de, geliştiricinin her bir üst projenin altına iç içe geçirebilmesine rağmen proje sayısı için bir sınır yoktur. Bu gruplandırma türü de özyinelemeli hale getirilebilir. Bu durumda, bir alt proje ile aynı türdeki projelerin alt öğesi olmak üzere alt öğesi olmak üzere alt öğe altında iç içe yerleştirilenebilir.

 İçe geçmiş proje iç parçası değildir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . İç içe geçme ve alt proje iç içe geçme özelliğini etkinleştirmek için kodu yazmanız gerekir. Üst proje, özel bir VSPackage veya proje türü oluşturup, proje iç içe geçirilmesi için gerekli kodu içeren kendi GUID 'sine sahip oluşturulup kaydedilir.

 [Nasıl yapılır: iç içe Projeler uygulama](../../extensibility/internals/how-to-implement-nested-projects.md)bölümünde proje iç içe geçme hakkında bir örnek bulabilirsiniz.

## <a name="nested-projects-example"></a>İç içe projeler örneği
 ![Iç Içe projeler çözümü](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects") İç içe projeler örneği

## <a name="see-also"></a>Ayrıca bkz.
- [İç İçe Projeleri Kaldırma ve Yeniden Yükleme Konusunda Dikkat Edilmesi Gerekenler](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [İç içe Projeler için Sihirbaz Desteği](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Proje ve Öğe Şablonlarını Kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)
- [İç içe Projeler için Komut İşlemesi Uygulama](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [İç içe Projeler için AddItem İletişim Kutusunu Filtreleme](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)
- [Yapılacaklar listesi: Yeni Proje Türleri Oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Bağlam Parametreleri](../../extensibility/internals/context-parameters.md)
- [Sihirbaz (.Vsz) Dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)
