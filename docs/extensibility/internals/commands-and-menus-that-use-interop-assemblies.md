---
title: Interop Montajları Kullanan Komutlar ve Menüler | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6c381abe9b4c6ea2a58342e185d7427fa56a180
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709483"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Interop derlemelerini kullanan komutlar ve menüler
Interop derlemelerini kullanarak menü ve araç çubuğu komutlarını uygulayan bir VSPackage şunları yapmalı:

- Tümleşik geliştirme ortamını [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (IDE) desteklediği komutlar ve şu anda etkin olup olmadıkları hakkında bilgilendirin.

- Komutları işlemek için kurallara (sözleşmeye) uyun.

- Açık ya <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> da <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> arabirim kullanarak komut işleme uygulayın.

  Aşağıdaki bölümde bu görevlerin nasıl yapılacağını açıklanmaktadır.

## <a name="in-this-section"></a>Bu bölümde
- [Interop derlemelerini kullanarak komut durumunu belirleme](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)

 VSPackage'ın IDE'ye hangi komutları desteklediğini ve şu anda etkin olup olmadığını nasıl not alabildiğini açıklar.

- [Interop meclislerinde komuta sözleşmeleri](../../extensibility/internals/command-contracts-in-interop-assemblies.md)

 Interop derlemelerini kullanarak komutları uygulayan tüm VSPackages tarafından kullanılan temel komut sözleşmesinin tanımını sağlar.

- [Komut uygulaması](../../extensibility/internals/command-implementation.md)

 VSPackage'ın komutu nasıl uyguladığına genel bir bakış sağlar.

- [Interop derleme komut işleyicilerini kaydedin](../../extensibility/internals/registering-interop-assembly-command-handlers.md)

 Bir VSPackage'ın komut işleyicisi sağladığını IDE'ye bildirmek için gereken kayıt defteri girişlerini açıklar.

## <a name="related-sections"></a>İlgili bölümler
- [Komut kullanılabilirliği](../../extensibility/internals/command-availability.md)

 Hangi VSPackage komutlarının kullanılabildiğini ve hangi nesnenin bunları işleyeceğini belirlemek için IDE tarafından kullanılan ölçütleri açıklar.

- [VSPackages kullanıcı arabirimi öğelerini nasıl ekler?](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Komut desteği kullanan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir Kullanıcı BirKullanıcı BirKullanıcı Bir Kullanıcı Ayrılığı nürü hakkında ayrıntılı

- [VSPackages komut yönlendirme](../../extensibility/internals/command-routing-in-vspackages.md)

 Bir nesneyi doğru komut isteğiyle ilişkilendirmek için kullanılan işlemin genel bakışı.
