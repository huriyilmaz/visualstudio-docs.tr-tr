---
title: Birlikte Çalışma Derlemeleri Kullanan Komutlar ve Menüler | Microsoft Docs
description: Birlikte çalışma derlemelerini kullanarak vsPackage'da menü ve araç çubuğu komutları uygulanırken tamamlanması gereken görevler hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0198490f6792654a95e9bea0f2b270dadd85a17e959a9817e0f74165a14a11bd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121432717"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Birlikte çalışma derlemelerini kullanan komutlar ve menüler
Birlikte çalışma derlemelerini kullanarak menü ve araç çubuğu komutları uygulayan bir VSPackage aşağıdakiler gerekir:

- Tümleşik [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geliştirme ortamını (IDE) desteklediği komutlar ve şu anda etkin olup olmadığı hakkında bilgilendirin.

- Komutları işleme kurallarına (sözleşme) uyun.

- veya arabirimini kullanarak komut işlemeyi açıkça <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> uygulama.

  Aşağıdaki bölümde bu görevlerin nasıl gerçekleştirllleri açıklanmış olur.

## <a name="in-this-section"></a>Bu bölümde
- [Birlikte çalışma derlemelerini kullanarak komut durumunu belirleme](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)

 BIR VSPackage'ın IDE'ye hangi komutları desteklediğini ve şu anda etkin olup olmadığını nasıl bilgileyeli olduğunu açıklar.

- [Birlikte çalışma derlemelerinde komut sözleşmeleri](../../extensibility/internals/command-contracts-in-interop-assemblies.md)

 Birlikte çalışma derlemelerini kullanarak komutları uygulayan tüm VSPackage'lar tarafından kullanılan temel komut sözleşmesinin tanımını sağlar.

- [Komut uygulaması](../../extensibility/internals/command-implementation.md)

 VSPackage'ın bir komutu nasıl uygulaydığını genel bir bakış sağlar.

- [Birlikte çalışma derlemesi komut işleyicilerini kaydetme](../../extensibility/internals/registering-interop-assembly-command-handlers.md)

 VSPackage'ın bir komut işleyicisi sağladığını IDE'ye bildirmek için gereken kayıt defteri girdilerini açıklar.

## <a name="related-sections"></a>İlgili bölümler
- [Komut kullanılabilirliği](../../extensibility/internals/command-availability.md)

 IDE tarafından hangi VSPackage komutlarının kullanılabilir olduğunu ve hangi nesnenin bunları işleyeni olduğunu belirlemek için kullanılan ölçütleri açıklar.

- [VSPackage'lar kullanıcı arabirimi öğelerini nasıl ekler?](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Komut desteğini kullanan bir kullanıcı arabirimi oluşturma hakkında [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ayrıntılar sağlar.

- [VSPackage'larda komut yönlendirme](../../extensibility/internals/command-routing-in-vspackages.md)

 Bir nesneyi doğru komut isteğiyle ilişkilendirmek için kullanılan işleme genel bakış.
