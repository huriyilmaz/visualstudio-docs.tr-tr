---
title: Çözümlere genel bakış
description: Visual Studio uzantılarında çözümlerle çalışmak isteyen uzantı geliştiricileri için bir çözümün iç işlevleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 914f1744accc10eb55cfb0b321a04560c27bca05
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069380"
---
# <a name="solutions-overview"></a>Çözümlere genel bakış

Bir çözüm, bir uygulama oluşturmak için birlikte çalışan bir veya daha fazla projenin gruplandırmasıdır. Çözümle ilgili proje ve durum bilgileri iki farklı çözüm dosyasında depolanır. [Çözüm (. sln) dosyası](solution-dot-sln-file.md) metin tabanlıdır ve kaynak kodu denetimi altına yerleştirilebilecek ve kullanıcılar arasında paylaşılabilir. [Çözüm Kullanıcı seçeneği (. suo) dosyası](solution-user-options-dot-suo-file.md) ikili. Sonuç olarak,. suo dosyası kaynak kodu denetimi altına yerleştirilemez ve kullanıcıya özgü bilgiler içerir.

Herhangi bir VSPackage, her iki çözüm dosyası türüne yazabilir. Dosyaların doğası nedeniyle, bunlara yazmak için uygulanan iki farklı arabirim vardır. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>Arabirim, metin bilgilerini. sln dosyasına yazar ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> arabirim ikili akışları. suo dosyasına yazar.

> [!NOTE]
> Projenin kendi kendine bir girdiyi çözüm dosyasına açıkça yazması gerekmez; ortam, proje için bunu işler. Bu nedenle, özellikle çözüm dosyasına ek içerik eklemek istemediğiniz müddetçe, VSPackage 'nizi bu şekilde kaydetmeniz gerekmez.

Çözüm kalıcılığını destekleyen her VSPackage, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> ortam tarafından uygulanan ve VSPackage ve ile çağrılan ve `IVsPersistSolutionProps` `IVsPersistSolutionOpts` her Ikisi de VSPackage tarafından uygulanan üç arabirim kullanır. `IVsPersistSolutionOpts`Arabirimin yalnızca özel bilgilerin, VSPackage tarafından. suo dosyasına yazılması durumunda uygulanması gerekir.

Bir çözüm açıldığında aşağıdaki işlem gerçekleşir.

1. Ortam çözümü okur.

2. Ortam bir bulursa `CLSID` , karşılık gelen VSPackage 'ı yükler.

3. Bir VSPackage yüklüyse, ortam `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> , VSPackage 'ın gerektirdiği arabirim için arabirim çağırır.

   - Bir. sln dosyasından okurken, ortam `QueryInterface` için çağırır `IVsPersistSolutionProps` .

   - Bir. suo dosyasından okurken, ortam `QueryInterface` için çağırır `IVsPersistSolutionOpts` .

   Bu dosyaların kullanımıyla ilgili belirli bilgiler [çözümde bulunabilir (. Sln) dosya](../../extensibility/internals/solution-dot-sln-file.md) ve [çözüm Kullanıcı seçenekleri (. Suo) dosyası](../../extensibility/internals/solution-user-options-dot-suo-file.md).

> [!NOTE]
> İki proje yapılandırmasından oluşan ve derlemeden üçüncü birini hariç tutarak yeni bir çözüm yapılandırması oluşturmak isterseniz, Kullanıcı arabirimi veya Otomasyonu özellik sayfaları ' nı kullanmanız gerekir. Çözüm yapı Yöneticisi yapılandırmalarının ve bunların özelliklerini doğrudan değiştiremezsiniz, ancak `SolutionBuild` Otomasyon MODELINDEKI DTE 'den sınıfını kullanarak çözüm yapı yöneticisini değiştirebilirsiniz. Çözümleri yapılandırma hakkında daha fazla bilgi için bkz. [çözüm yapılandırması](../../extensibility/internals/solution-configuration.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
