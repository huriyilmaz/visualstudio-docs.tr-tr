---
title: Kaynak Denetimi Tümleştirme temel | Microsoft Docs
description: Kaynak denetimi eklentisi ve VSPackage tabanlı Visual Studio çözümü olmak üzere iki tür kaynak denetimi tümleştirmesi hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 00015c08a95e0fea62911942f996817d115ceaeedc04a677dfc2cc36597d78db
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401173"
---
# <a name="source-control-integration-essentials"></a>Kaynak Denetimini Tümleştirme Temel Bileşenleri
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] iki tür kaynak denetimi tümleştirmesini destekler: temel işlevsellik sağlayan ve Kaynak Denetimi Eklentisi API'si (eski adıyla MSSCCI API'si) kullanılarak inşa edilen bir kaynak denetimi eklentisi ve daha sağlam işlevsellik sağlayan VSPackage tabanlı bir kaynak denetimi tümleştirme çözümü.

## <a name="source-control-plug-in"></a>Kaynak Denetimi Eklentisi
 Kaynak Denetimi Eklentisi, Kaynak Denetimi Eklentisi API'sini uygulayan bir DLL olarak yazılır. Kayıt ve kaynak denetimi tümleştirme işlevselliği API aracılığıyla sağlanır. Bu yaklaşımın uygulanması, VSPackage kaynak denetiminden daha kolaydır ve çoğu kaynak denetimi işlemleri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] için kullanıcı arabirimini (UI) kullanır.

 Kaynak Denetimi Eklentisi API'sini kullanarak bir kaynak denetimi eklentisi uygulamak için şu adımları izleyin:

1. Kaynak Denetimi Eklentileri'ne belirtilen işlevleri [uygulayan bir](../../extensibility/source-control-plug-ins.md)DLL oluşturun.

2. Nasıl: Kaynak Denetimi Eklentisi Yükleme konusunda açıklandığı gibi, uygun kayıt defteri [girdilerini yaparak DLL'i kaydetme.](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)

3. Bir yardımcı kullanıcı arabirimi oluşturun ve Kaynak Denetim Bağdaştırıcısı Paketi (kaynak denetimi eklentileri aracılığıyla kaynak denetimi işlevselliğini ele alan bileşen) istendiğinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bunu görüntüler.

   Daha fazla bilgi için [bkz. Kaynak Denetimi Eklentisi Oluşturma.](../../extensibility/internals/creating-a-source-control-plug-in.md)

## <a name="source-control-vspackage"></a>Kaynak Denetimi VSPackage
 Kaynak denetimi VSPackage uygulaması, kaynak denetimi kullanıcı arabirimi için özelleştirilmiş bir değiştirme [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geliştirmenize olanak sağlar. Bu yaklaşım, kaynak denetimi tümleştirmesi üzerinde tam denetim sağlar, ancak ui öğelerini sağlamanız ve aksi takdirde eklenti yaklaşımı altında sağlanacak kaynak denetim arabirimlerini uygulamanız gerekir.

 VSPackage kaynak denetimi uygulamak için şunları gerçekleştirin:

1. Kayıt ve Seçim içinde açıklandığı gibi kendi kaynak denetimi VSPackage'nizi [oluşturun ve kaydettirin.](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)

2. Varsayılan kaynak denetimi kullanıcı arabirimini özel kullanıcı arabiriminiz ile değiştirin. Bkz. [Özel Kullanıcı Arabirimi.](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)

3. Kullanılacak glyph'leri belirtin ve **Çözüm Gezgini** işlemek. Bkz. [Glyph Denetimi.](../../extensibility/internals/glyph-control-source-control-vspackage.md)

4. Sorgu Düzenleme SorguSunu Kaydet'te gösterildiği gibi Sorgu Düzenleme ve [Sorgu Kaydetme olaylarını işle.](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)

   Daha fazla bilgi için [bkz. Kaynak Denetimi VSPackage Oluşturma.](../../extensibility/internals/creating-a-source-control-vspackage.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Genel Bakış](../../extensibility/internals/source-control-integration-overview.md)
- [Kaynak Denetimi Eklentisi Oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Kaynak Denetimi VSPackage’ı Oluşturma](../../extensibility/internals/creating-a-source-control-vspackage.md)
