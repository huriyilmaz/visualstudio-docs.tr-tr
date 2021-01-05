---
title: Tek dosya oluşturanlar kaydediliyor | Microsoft Docs
description: Visual Studio 'da özel bir aracın örneğini oluşturmak ve belirli bir proje türüyle ilişkilendirmek için nasıl kaydedeceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a0ce4afeddebdec8519467e1f4249095ce98f6b
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875264"
---
# <a name="registering-single-file-generators"></a>Tek Dosya Oluşturucuları Kaydetme
Özel bir aracın ' de kullanılabilmesini sağlamak için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , onu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] örneklendirilecek ve belirli bir proje türüyle ilişkilenbilmeniz için kaydetmeniz gerekir.

### <a name="to-register-a-custom-tool"></a>Özel bir araç kaydetmek için

1. Özel araç DLL 'sini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yerel kayıt defterinde veya sistem kayıt defterinde, HKEY_CLASSES_ROOT altına kaydedin.

    Örneğin, aşağıda verilen yönetilen MSDataSetGenerator özel aracı için kayıt bilgileri verilmiştir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] :

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]
   @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"
   "ThreadingModel"="Both"
   "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"
   ```

2. İstenen Hive içindeki bir kayıt defteri anahtarını [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \\ , *GUID* 'in belirli dilin proje sistemi veya hizmeti tarafından tanımlanan GUID olduğu,*Bu GUID* 'nin altında yer aldığı bir kayıt defteri anahtarı oluşturun. Anahtarın adı, özel aracınıza ait programlı ad olur. Özel araç anahtarı aşağıdaki değerlere sahiptir:

   - (Varsayılan)

        İsteğe bağlı. Özel araç için Kullanıcı dostu bir açıklama sağlar. Bu parametre isteğe bağlıdır, ancak önerilir.

   - IN

        Gereklidir. Uygulayan COM bileşeni sınıf kitaplığının tanımlayıcısını belirtir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> .

   - GeneratesDesignTimeSource

        Gereklidir. Bu özel araç tarafından üretilen dosyalardaki türlerin görsel tasarımcılar tarafından kullanılabilir duruma getirilmeyeceğini gösterir. Görsel tasarımcılarda kullanılabilir olan türler için bu parametrenin değerinin (sıfır) 0 olması gerekir.

   > [!NOTE]
   > Özel aracının kullanılabilir olmasını istediğiniz her dil için özel aracı ayrı olarak kaydetmeniz gerekir.

    Örneğin, MSDataSetGenerator her dil için kendisini bir kez kaydeder:

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]
   @="Microsoft VB Code Generator for XSD"
   "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"
   "GeneratesDesignTimeSource"=dword:00000001

   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]
   @="Microsoft C# Code Generator for XSD"
   "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"
   "GeneratesDesignTimeSource"=dword:00000001
   ```

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>
- [Tek Dosya Oluşturucular Ekleme](../../extensibility/internals/implementing-single-file-generators.md)
- [Türleri Görsel Tasarımcıların Kullanımına Sunma](../../extensibility/internals/exposing-types-to-visual-designers.md)
- [BuildManager nesnesine giriş](/previous-versions/8f9kffa8(v=vs.140))