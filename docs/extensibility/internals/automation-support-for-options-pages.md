---
title: Seçenekler sayfaları için Otomasyon desteği | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03360bfc01110e7b4ef73956f0199aaaed9cee2c
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848966"
---
# <a name="automation-support-for-options-pages"></a>Seçenekler sayfaları için Otomasyon desteği
VSPackages, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ' de **Araçlar** menüsüne (**Araçlar seçenekleri** sayfaları) özel **Seçenekler** iletişim kutuları sağlayabilir ve bunları otomasyon modeli için kullanılabilir hale getirir.

## <a name="tools-options-pages"></a>Araçlar Seçenekler sayfaları
 Bir **araç seçenekleri** sayfası oluşturmak için, bir vspackage, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> yönteminin VSPackage uygulamasının aracılığıyla ortama döndürülen bir kullanıcı denetim uygulamasını sağlamalıdır. (Veya, yönetilen kod için <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> yöntemi.)

 Bu yeni sayfaya otomasyon modeli aracılığıyla erişime izin vermek için isteğe bağlıdır, ancak önemle önerilir. Bunu aşağıdaki adımlarla yapabilirsiniz:

1. <xref:EnvDTE._DTE.Properties%2A> nesnesini IDispatch ile türetilmiş bir nesnenin uygulamasıyla genişletin.

2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> yönteminin (veya yönetilen kod için <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> yöntemi) bir uygulamasını IDispatch ile türetilmiş nesneye döndürün.

3. Bir Otomasyon tüketicisi özel bir **seçenek** özelliği sayfasında <xref:EnvDTE._DTE.Properties%2A> yöntemini çağırdığında, ortam, özel bir **araç seçenekleri** sayfasının otomasyon uygulamasını elde etmek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> yöntemini kullanır.

4. VSPackage Otomasyon nesnesi, <xref:EnvDTE._DTE.Properties%2A>tarafından döndürülen her bir <xref:EnvDTE.Property> sağlamak için kullanılır.

   Özel bir **Araçlar Seçenekler** sayfası uygulayan bir örnek için bkz. [VSSDK örnekleri](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Ayrıca bkz.
- [Proje nesnelerini kullanıma sunma](../../extensibility/internals/exposing-project-objects.md)
