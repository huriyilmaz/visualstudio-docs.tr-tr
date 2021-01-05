---
title: Kaynak denetimi tümleştirme temelleri | Microsoft Docs
description: "Visual Studio 'nun desteklediği iki kaynak denetimi tümleştirmesi türü hakkında bilgi edinin: kaynak denetimi eklentisi ve VSPackage tabanlı kaynak denetimi çözümü."
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: a4dd5186b20dfac4ad5a027e4519700ff8ac1f77
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876044"
---
# <a name="source-control-integration-essentials"></a>Kaynak Denetimini Tümleştirme Temel Bileşenleri
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] iki tür kaynak denetimi tümleştirmesini destekler: temel işlevselliği sağlayan ve kaynak denetim eklentisi API 'SI (eski adıyla MSSCCı API) kullanılarak oluşturulan ve daha sağlam işlevsellik sağlayan VSPackage tabanlı bir kaynak denetimi tümleştirme çözümü.

## <a name="source-control-plug-in"></a>Kaynak denetimi eklentisi
 Kaynak denetimi eklentisi, kaynak denetimi eklentisi API 'sini uygulayan DLL olarak yazılır. Kayıt ve kaynak denetimi tümleştirme işlevselliği API aracılığıyla sağlanır. Bu yaklaşım, bir kaynak denetimi VSPackage uygulaması daha kolaydır ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaynak denetimi işlemleri için Kullanıcı arabirimini (UI) kullanır.

 Kaynak denetimi eklentisi API 'sini kullanarak bir kaynak denetimi eklentisi uygulamak için aşağıdaki adımları izleyin:

1. [Kaynak denetimi eklentilerinde](../../extensibility/source-control-plug-ins.md)belirtilen işlevleri uygulayan bir DLL oluşturun.

2. DLL 'yi, [nasıl yapılır: kaynak denetimi eklentisi yüklemesi](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)bölümünde açıklandığı gibi uygun kayıt defteri girdilerini yaparak kaydettirin.

3. Bir yardımcı Kullanıcı arabirimi oluşturun ve kaynak denetim bağdaştırıcısı paketi (kaynak denetimi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] eklentileri aracılığıyla kaynak denetimi işlevini işleyen bileşen) tarafından istendiğinde görüntüleyin.

   Daha fazla bilgi için bkz. [kaynak denetim eklentisi oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md).

## <a name="source-control-vspackage"></a>Kaynak denetimi VSPackage
 Kaynak denetimi VSPackage uygulamasının, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaynak denetimi kullanıcı arabirimi için özelleştirilmiş bir değiştirme geliştirmenize olanak sağlar. Bu yaklaşım, kaynak denetimi tümleştirmesi üzerinde tam denetim sağlar, ancak kullanıcı arabirimi öğelerini sağlamanızı ve başka türlü eklenti yaklaşımı altında sağlanacak kaynak denetimi arabirimlerini uygulamanızı gerektirir.

 Bir kaynak denetimi VSPackage uygulamak için şunları yapmanız gerekir:

1. [Kayıt ve seçim](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)bölümünde açıklandığı gibi kendi kaynak denetimi VSPackage 'ı oluşturun ve kaydedin.

2. Varsayılan kaynak denetimi kullanıcı arabirimini Özel UI 'iyle değiştirin. Bkz. [Özel Kullanıcı arabirimi](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).

3. Kullanılacak glifleri belirtin ve **Çözüm Gezgini** glif olaylarını işleyin. Bkz. [glif denetimi](../../extensibility/internals/glyph-control-source-control-vspackage.md).

4. Sorgu [düzenleme sorgu kaydetme](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)bölümünde gösterildiği gibi, sorgu düzenleme ve sorgu kaydetme olaylarını işle.

   Daha fazla bilgi için bkz. [kaynak denetimi VSPackage oluşturma](../../extensibility/internals/creating-a-source-control-vspackage.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Genel Bakış](../../extensibility/internals/source-control-integration-overview.md)
- [Kaynak Denetimi Eklentisi Oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Kaynak Denetimi VSPackage’ı Oluşturma](../../extensibility/internals/creating-a-source-control-vspackage.md)
