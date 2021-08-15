---
title: Seçenekler Sayfaları için Otomasyon Desteği | Microsoft Docs
description: VSPackage'larda özel Araç Seçenekleri sayfalarınızı otomatik otomasyon modeline Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 7f8157f94121799d9b75874f4a5ee9a4724162247c9ff8dea3bdf52ff87e210d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121432728"
---
# <a name="automation-support-for-options-pages"></a>Seçenekler sayfaları için otomasyon desteği
VSPackage'lar'  içinde Araçlar  menüsüne **(Araçlar** Seçenekler sayfaları) özel Seçenekler iletişim kutuları sağlar ve bunları otomasyon modeli için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kullanılabilir hale ayarlayabilir.

## <a name="tools-options-pages"></a>Araçlar Seçenekler sayfaları
 Bir Araç **Seçenekleri sayfası oluşturmak** için VSPackage, vsPackage'ın yöntemi uygulaması aracılığıyla ortama döndürülen bir kullanıcı denetimi uygulaması <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> sağlamalıdır. (Veya yönetilen kod için <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> yöntemi.)

 Otomasyon modeli aracılığıyla bu yeni sayfaya erişim izni vermek isteğe bağlıdır ancak kesinlikle teşvik edilecektir. Bunu aşağıdaki adımlarla yapabilirsiniz:

1. <xref:EnvDTE._DTE.Properties%2A>IDispatch türetilmiş bir nesnenin uygulaması aracılığıyla nesneyi genişletin.

2. Yöntemin bir uygulamasını <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> (veya yönteminin yönetilen kodu <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> için) IDispatch türetilmiş nesnesine geri döner.

3. Otomasyon tüketicisi özel bir Seçenek özellik sayfasında yöntemini çağırsa, ortam özel Araçlar Seçenekleri sayfasının otomasyon uygulamasını almak <xref:EnvDTE._DTE.Properties%2A> için yöntemini  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> kullanır. 

4. VsPackage otomasyon nesnesi daha sonra tarafından döndürülen her bir sağlamak <xref:EnvDTE.Property> için <xref:EnvDTE._DTE.Properties%2A> kullanılır.

   Özel Araçlar Seçenekleri sayfasını uygulayan **bir örnek için** bkz. [VSSDK Örnekleri](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Ayrıca bkz.
- [Proje nesnelerini açığa çıkarma](../../extensibility/internals/exposing-project-objects.md)
