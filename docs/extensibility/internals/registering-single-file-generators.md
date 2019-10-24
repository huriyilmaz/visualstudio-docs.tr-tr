---
title: Tek dosya oluşturanlar kaydediliyor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e9026da08272d69bac246f98ae741a47527d627f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724561"
---
# <a name="registering-single-file-generators"></a>Tek Dosya Oluşturucuları Kaydetme
Özel bir aracı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ' de kullanılabilir hale getirmek için, bu dosyayı örneklendirilecek ve belirli bir proje türüyle ilişkilendiye [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaydetmeniz gerekir.

### <a name="to-register-a-custom-tool"></a>Özel bir araç kaydetmek için

1. Özel araç DLL 'sini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yerel kayıt defterinde veya sistem kayıt defteri 'nde HKEY_CLASSES_ROOT altında kaydedin.

    Örneğin, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ile birlikte yönetilen MSDataSetGenerator özel aracı için kayıt bilgileri aşağıda verilmiştir:

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]
   @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"
   "ThreadingModel"="Both"
   "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"
   ```

2. *GUID* 'nin belirli bir dilin proje sistemi veya hizmeti tarafından tanımlanan*GUID olduğu, istenen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \\ Hive* içindeki bir kayıt defteri anahtarı oluşturun. Anahtarın adı, özel aracınıza ait programlı ad olur. Özel araç anahtarı aşağıdaki değerlere sahiptir:

   - (Varsayılan)

        İsteğe bağlı. Özel araç için Kullanıcı dostu bir açıklama sağlar. Bu parametre isteğe bağlıdır, ancak önerilir.

   - IN

        Gerekli. @No__t_0 uygulayan COM bileşeni sınıf kitaplığının tanımlayıcısını belirtir.

   - GeneratesDesignTimeSource

        Gerekli. Bu özel araç tarafından üretilen dosyalardaki türlerin görsel tasarımcılar tarafından kullanılabilir duruma getirilmeyeceğini gösterir. Görsel tasarımcılarda kullanılabilir olan türler için bu parametrenin değerinin (sıfır) 0 olması gerekir.

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
- [BuildManager nesnesine giriş](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)