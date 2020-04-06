---
title: Kaynak Kontrol Entegrasyon Esasları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e56658d644720f1563d71d3d08bf35268119112f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705232"
---
# <a name="source-control-integration-essentials"></a>Kaynak Denetimini Tümleştirme Temel Bileşenleri
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]iki tür kaynak denetimi tümleştirmesini destekler: temel işlevsellik sağlayan ve Kaynak Denetimi Eklentisi API (eski adıyla MSSCCI API olarak bilinir) kullanılarak oluşturulmuş bir kaynak denetim eklentisi ve daha sağlam işlevsellik sağlayan VSPackage tabanlı kaynak denetim tümleştirme çözümü.

## <a name="source-control-plug-in"></a>Kaynak Kontrol Eklentisi
 Kaynak Denetim Eklentisi, Kaynak Denetimi Eklentisi API'sini uygulayan bir DLL olarak yazılır. Kayıt ve kaynak denetimi tümleştirme işlevi API aracılığıyla sağlanır. Bu yaklaşımın uygulanması bir kaynak denetimi VSPackage daha [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kolaydır ve çoğu kaynak denetim işlemleri için kullanıcı arabirimi (UI) kullanır.

 Kaynak Denetimi Eklentisi API'sini kullanarak kaynak denetimi eklentisi uygulamak için aşağıdaki adımları izleyin:

1. [Kaynak Denetim Eklentilerinde](../../extensibility/source-control-plug-ins.md)belirtilen işlevleri uygulayan bir DLL oluşturun.

2. Nasıl açıklandığı gibi uygun kayıt defteri girişleri yaparak DLL [kaydolun: Bir Kaynak Denetim Eklentisi yükleyin.](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)

3. Bir yardımcı ui oluşturun ve Kaynak Denetim Bağdaştırıcı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Paketi (kaynak denetimi eklentileri aracılığıyla kaynak denetimi işlevselliğini işleyen bileşen) tarafından istendiğinde onu görüntüleyin.

   Daha fazla bilgi için kaynak [denetimi eklentisi oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)konusuna bakın.

## <a name="source-control-vspackage"></a>Kaynak Kontrol VSPackage
 Bir kaynak denetimi VSPackage uygulaması kaynak denetimi Kullanıcı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Arabirimi için özelleştirilmiş bir yedek geliştirmenize olanak sağlar. Bu yaklaşım, kaynak denetimi tümleştirmesi üzerinde tam denetim sağlar, ancak kullanıcı arabirimi öğelerini sağlamanızı ve aksi takdirde eklenti yaklaşımı altında sağlanacak kaynak denetim arabirimlerini uygulamanızı gerektirir.

 Bir kaynak denetimi VSPackage uygulamak için, gerekir:

1. Kayıt ve [Seçim'de](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)açıklandığı gibi kendi kaynak denetimi vspackage oluşturun ve kaydedin.

2. Varsayılan kaynak denetimi kullanıcı kullanıcı sını özel kullanıcı bilgilerinizle değiştirin. Bkz. [Özel Kullanıcı Arabirimi.](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)

3. Kullanılacak glifleri belirtin ve **Çözüm Gezgini** glyph olaylarını işleyin. Bkz. [Glyph Control](../../extensibility/internals/glyph-control-source-control-vspackage.md).

4. Sorgu Tut Sorgu Tut ve Sorgu Kaydet olaylarını [sorgula, Sorgu'u Edit Sorgu kaydet'te](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)gösterildiği gibi kaydet.

   Daha fazla bilgi için kaynak [denetimi VSPackage oluşturma](../../extensibility/internals/creating-a-source-control-vspackage.md)konusuna bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Genel bakış](../../extensibility/internals/source-control-integration-overview.md)
- [Kaynak Denetimi Eklentisi Oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Kaynak Denetimi VSPackage’ı Oluşturma](../../extensibility/internals/creating-a-source-control-vspackage.md)
