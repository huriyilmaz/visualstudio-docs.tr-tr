---
title: Projeleri İç İçe | Microsoft Docs
description: VSPackage'nızı kullanan uygulama geliştiricilerinin benzer proje türlerini aynı proje türlerinde gruplamalarına olanak sağlayan projeleri iç içe yerleştirme hakkında Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 86998a5af95a8c8460bfe70c09bc456bde37701d06d1a382663c0c7d83f139ab
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121321330"
---
# <a name="nesting-projects"></a>Projeleri İç İçe Geçirme
Enterprise paketinizi kullanan uygulama geliştiricileri, benzer proje türlerini içinde proje iç içe yerleştirmeyi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kullanarak *rahatça birlikte gruplamanızı sağlar.* Örneğin, Enterprise Şablon projesi, projeleri kategorilere gruplamak için iç içe projeler kullanır. İş cephesi projeleri, Web UI projeleri ve diğer projeler tek bir kategoride gruplanmıştır.

 Bu senaryoda, geliştiricinin her üst proje altında iç içe yer alan proje sayısına yönelik bir sınır yoktur, ancak geliştirici program aracılığıyla sınırlar sağlaysa da. Bu tür bir gruplama da, bir alt projeyle aynı türde projeler alt projenin altında iç içe iç içe yer alan alt öğenin alt projesi (üst projenin bir alt projesi) haline dönüşerek yineli hale de olabilir.

 Project iç içe yerleştirme, iç kısımlardan biri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] değildir. Alt projeler içinde iç içe yerleştirmeyi ve alt proje iç içe yerleştirmeyi etkinleştirmek için kodu yazmanız gerekir. Üst proje, proje iç içe yerleştirmeyi uygulamak için gereken kodu içeren kendi GUID'si ile oluşturulan ve kaydedilen özel bir VSPackage veya proje t t'dır.

 Projeleri iç içe yerleştirme ile ilgili bir örneği Nasıl edn: İç içe projeler [uygulama içinde bulabilirsiniz.](../../extensibility/internals/how-to-implement-nested-projects.md)

## <a name="nested-projects-example"></a>İç içe projeler örneği
 ![İç İçe Projeler Çözümü](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects") İç içe projeler örneği

## <a name="see-also"></a>Ayrıca bkz.
- [İç İçe Projeleri Kaldırma ve Yeniden Yükleme Konusunda Dikkat Edilmesi Gerekenler](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [İç içe Projeler için Sihirbaz Desteği](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Proje ve Öğe Şablonlarını Kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)
- [İç içe Projeler için Komut İşlemesi Uygulama](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [İç içe Projeler için AddItem İletişim Kutusunu Filtreleme](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)
- [Yapılacaklar listesi: Yeni Proje Türleri Oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Bağlam Parametreleri](../../extensibility/internals/context-parameters.md)
- [Sihirbaz (.Vsz) Dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)
