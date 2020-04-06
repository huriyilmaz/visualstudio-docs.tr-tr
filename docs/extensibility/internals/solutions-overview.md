---
title: Çözümlere genel bakış
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 767db749d953855cd5c6f81f356a195c830aa838
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705308"
---
# <a name="solutions-overview"></a>Çözümlere genel bakış

Çözüm, bir uygulama oluşturmak için birlikte çalışan bir veya daha fazla projenin gruplandırmasıdır. Çözümle ilgili proje ve durum bilgileri iki farklı çözüm dosyasında saklanır. [Çözüm (.sln) dosyası](solution-dot-sln-file.md) metin tabanlıdır ve kaynak kodu denetimi altına yerleştirilebilir ve kullanıcılar arasında paylaşılabilir. [Çözüm kullanıcı seçeneği (.suo) dosyası](solution-user-options-dot-suo-file.md) ikilidir. Sonuç olarak, .suo dosyası kaynak kodu denetimi altına yerleştirilemez ve kullanıcıya özel bilgiler içerir.

Herhangi bir VSPackage çözüm dosyası nın her iki türüne de yazabilirsiniz. Dosyaların doğası nedeniyle, onlara yazmak için uygulanan iki farklı arabirim vardır. Arayüz <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> .sln dosyasına metin bilgilerini <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> yazar ve arayüz .suo dosyasına ikili akışlar yazar.

> [!NOTE]
> Bir proje açıkça çözüm dosyasına kendisi için bir giriş yazmak zorunda değildir; çevre proje için bunu işler. Bu nedenle, çözüm dosyasına özel olarak ek içerik eklemek istemediğiniz sürece, VSPackage'ınızı bu şekilde kaydetmeniz gerekmez.

Her VSPackage destekleyici çözüm kalıcılığı üç <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> arayüz kullanır, çevre tarafından uygulanan ve VSPackage tarafından `IVsPersistSolutionProps` `IVsPersistSolutionOpts`çağrılan arayüz, ve , her ikisi de VSPackage tarafından uygulanır. Arayüz `IVsPersistSolutionOpts` yalnızca VSPackage tarafından .suo dosyasına özel bilgilerin yazılması gerekiyorsa uygulanması gerekir.

Bir çözüm açıldığında, aşağıdaki işlem gerçekleşir.

1. Ortam çözümü okur.

2. Ortam bir `CLSID`, ilgili VSPackage yükler bulur.

3. Bir VSPackage yüklenirse, `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> ortam VSPackage'ın gerektirdiği arabirim için arayüz gerektirir.

   - Bir .sln dosyasından okurken, `QueryInterface` ortam `IVsPersistSolutionProps`.

   - Bir .suo dosyasından okurken, `QueryInterface` ortam `IVsPersistSolutionOpts`.

   Bu dosyaların kullanımına ilişkin özel bilgiler [Solution (. Sln) Dosya](../../extensibility/internals/solution-dot-sln-file.md) ve [Çözüm Kullanıcı Seçenekleri (. Suo) Dosya](../../extensibility/internals/solution-user-options-dot-suo-file.md).

> [!NOTE]
> İki projenin yapılandırmalarından oluşan ve üçte birini yapıdan hariç talan eden yeni bir çözüm yapılandırması oluşturmak istiyorsanız, Özellik Sayfaları Web'ini veya otomasyonu kullanmanız gerekir. Çözüm yapı yöneticisi yapılandırmalarını ve özelliklerini doğrudan değiştiremezsiniz, ancak otomasyon modelinde `SolutionBuild` DTE'deki sınıfı kullanarak çözüm yapı yöneticisini değiştirebilirsiniz. Çözümleri yapılandırma hakkında daha fazla bilgi için [Çözüm Yapılandırması'na](../../extensibility/internals/solution-configuration.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
