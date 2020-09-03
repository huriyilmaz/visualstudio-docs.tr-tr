---
title: Kaynak denetimi tümleştirme temelleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b9189b647baa29d72975f84172696ecb54cd7f87
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183426"
---
# <a name="source-control-integration-essentials"></a>Kaynak Denetimini Tümleştirme Temel Bileşenleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] iki tür kaynak denetimi tümleştirmesini destekler: temel işlevselliği sağlayan ve kaynak denetim eklentisi API 'SI (eski adıyla MSSCCı API) kullanılarak oluşturulan ve daha sağlam işlevsellik sağlayan VSPackage tabanlı bir kaynak denetimi tümleştirme çözümü.  
  
## <a name="source-control-plug-in"></a>Kaynak denetimi eklentisi  
 Kaynak denetimi eklentisi, kaynak denetimi eklentisi API 'sini uygulayan DLL olarak yazılır. Kayıt ve kaynak denetimi tümleştirme işlevselliği API aracılığıyla sağlanır. Bu yaklaşım, bir kaynak denetimi VSPackage uygulaması daha kolaydır ve [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kaynak denetimi işlemleri için Kullanıcı arabirimini (UI) kullanır.  
  
 Kaynak denetimi eklentisi API 'sini kullanarak bir kaynak denetimi eklentisi uygulamak için aşağıdaki adımları izleyin:  
  
1. [Kaynak denetimi eklentilerinde](../../extensibility/source-control-plug-ins.md)belirtilen işlevleri uygulayan bir DLL oluşturun.  
  
2. DLL 'yi, [nasıl yapılır: kaynak denetimi eklentisi yüklemesi](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)bölümünde açıklandığı gibi uygun kayıt defteri girdilerini yaparak kaydettirin.  
  
3. Bir yardımcı Kullanıcı arabirimi oluşturun ve kaynak denetim bağdaştırıcısı paketi (kaynak denetimi [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] eklentileri aracılığıyla kaynak denetimi işlevini işleyen bileşen) tarafından istendiğinde görüntüleyin.  
  
   Daha fazla bilgi için bkz. [kaynak denetim eklentisi oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md).  
  
## <a name="source-control-vspackage"></a>Kaynak denetimi VSPackage  
 Kaynak denetimi VSPackage uygulamasının, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kaynak denetimi kullanıcı arabirimi için özelleştirilmiş bir değiştirme geliştirmenize olanak sağlar. Bu yaklaşım, kaynak denetimi tümleştirmesi üzerinde tam denetim sağlar, ancak kullanıcı arabirimi öğelerini sağlamanızı ve başka türlü eklenti yaklaşımı altında sağlanacak kaynak denetimi arabirimlerini uygulamanızı gerektirir.  
  
 Bir kaynak denetimi VSPackage uygulamak için şunları yapmanız gerekir:  
  
1. [Kayıt ve seçim](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)bölümünde açıklandığı gibi kendi kaynak denetimi VSPackage 'ı oluşturun ve kaydedin.  
  
2. Varsayılan kaynak denetimi kullanıcı arabirimini Özel UI 'iyle değiştirin. Bkz. [Özel Kullanıcı arabirimi](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).  
  
3. Kullanılacak glifleri belirtin ve **Çözüm Gezgini** glif olaylarını işleyin. Bkz. [glif denetimi](../../extensibility/internals/glyph-control-source-control-vspackage.md).  
  
4. Sorgu [düzenleme sorgu kaydetme](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)bölümünde gösterildiği gibi, sorgu düzenleme ve sorgu kaydetme olaylarını işle.  
  
   Daha fazla bilgi için bkz. [kaynak denetimi VSPackage oluşturma](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bakýþ](../../extensibility/internals/source-control-integration-overview.md)   
 [Kaynak denetimi eklentisi oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Kaynak Denetimi VSPackage’ı Oluşturma](../../extensibility/internals/creating-a-source-control-vspackage.md)
