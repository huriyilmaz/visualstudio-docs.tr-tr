---
title: Seçenekler sayfaları için Otomasyon desteği | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709928"
---
# <a name="automation-support-for-options-pages"></a>Seçenekler sayfaları için Otomasyon desteği
VSPackages, ' de **Araçlar** menüsüne (**Araçlar seçenekleri** sayfaları) özel **Seçenekler** iletişim kutuları sunabilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve bunları otomasyon modeli için kullanılabilir hale getirir.

## <a name="tools-options-pages"></a>Araçlar Seçenekler sayfaları
 Bir **araç seçenekleri** sayfası oluşturmak için, bir VSPackage, yöntemin VSPackage 'un uygulamasıyla bir kullanıcı denetimi uygulamasını döndürmelidir <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> . (Veya, yönetilen kod için <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> yöntemi için.)

 Bu yeni sayfaya otomasyon modeli aracılığıyla erişime izin vermek için isteğe bağlıdır, ancak önemle önerilir. Bunu aşağıdaki adımlarla yapabilirsiniz:

1. <xref:EnvDTE._DTE.Properties%2A>Nesneyi IDispatch ile türetilmiş bir nesnenin uygulamasıyla genişletin.

2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>Metodun (veya yönetilen kod için) bir uygulamasını <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> IDispatch 'ten türetilmiş nesneye döndürün.

3. Bir Otomasyon tüketicisi <xref:EnvDTE._DTE.Properties%2A> özel bir **seçenek** özelliği sayfasında yöntemini çağırdığında, ortam <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> yöntemini kullanarak özel bir **araç seçenekleri** sayfasının otomasyon uygulamasını elde eder.

4. VSPackage Otomasyon nesnesi, tarafından döndürülen her bir sağlamak için kullanılır <xref:EnvDTE.Property> <xref:EnvDTE._DTE.Properties%2A> .

   Özel bir **Araçlar Seçenekler** sayfası uygulayan bir örnek için bkz. [VSSDK örnekleri](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Ayrıca bkz.
- [Proje nesnelerini kullanıma sunma](../../extensibility/internals/exposing-project-objects.md)
