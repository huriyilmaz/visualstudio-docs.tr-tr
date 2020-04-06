---
title: Seçenekler Sayfaları için Otomasyon Desteği | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe45238948d5b4cdebbf9f002f6b242515e7622e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709928"
---
# <a name="automation-support-for-options-pages"></a>Seçenekler sayfaları için otomasyon desteği
VSPackages, **Araçlar** menüsüne özel **Seçenekler** iletişim kutuları **(Araçlar Seçenekleri** sayfaları) sağlayabilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve bunları otomasyon modeline sunabilir.

## <a name="tools-options-pages"></a>Araçlar Seçenekler sayfaları
 **Bir Araç Seçenekleri** sayfası oluşturmak için, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> VSPackage'ın VSPackage'ın yöntemin uygulanması yoluyla ortama döndürülen bir kullanıcı denetimi uygulaması sağlaması gerekir. (Veya yönetilen kod için <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> yöntem.)

 Otomasyon modeli aracılığıyla bu yeni sayfaya erişime izin vermek isteğe bağlıdır, ancak şiddetle teşvik edileblidir. Bunu aşağıdaki adımlarla yapabilirsiniz:

1. IDispatch <xref:EnvDTE._DTE.Properties%2A> türetilmiş bir nesnenin uygulanması yoluyla nesneyi genişletin.

2. Yöntemin <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> bir uygulamasını (veya yönetilen <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> kod yöntemi için) IDispatch türetilmiş nesneye döndürün.

3. Otomasyon tüketicisi <xref:EnvDTE._DTE.Properties%2A> yöntemi özel bir **Seçenek** özelliği sayfasında <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> aradığında, ortam özel **araçlar seçenekleri** sayfasının otomasyon uygulamasını elde etmek için yöntemi kullanır.

4. VSPackage otomasyon nesnesi daha sonra <xref:EnvDTE.Property> her <xref:EnvDTE._DTE.Properties%2A>tarafından döndürülen sağlamak için kullanılır.

   Özel **Araçlar Seçenekleri** sayfasını uygulayan bir örnek için [VSSDK Örnekleri'ne](https://github.com/Microsoft/VSSDK-Extensibility-Samples)bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Proje nesnelerini açığa çıkarma](../../extensibility/internals/exposing-project-objects.md)
