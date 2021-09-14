---
title: Tek Dosya Oluşturucuları | Microsoft Docs
description: Örnek oluşturmak ve belirli bir proje Visual Studio ilişkilendirmek için özel bir aracı Visual Studio aracı kaydetmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ad56731f0e0432dea2eb583d23dcf4285801e2f6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725014"
---
# <a name="registering-single-file-generators"></a>Tek Dosya Oluşturucuları Kaydetme
içinde özel bir aracın kullanılabilir olması için, örneği oluşturmak ve belirli bir proje türüyle ilişkilendirip bunu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaydetmek gerekir.

### <a name="to-register-a-custom-tool"></a>Özel bir aracı kaydetmek için

1. Özel araç DLL'sini yerel kayıt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] defterine veya sistem kayıt defterine, HKEY_CLASSES_ROOT.

    Örneğin, ile birlikte gelen yönetilen MSDataSetGenerator özel aracına ilişkin kayıt bilgileri aşağıda [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verilmektedir:

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]
   @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"
   "ThreadingModel"="Both"
   "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"
   ```

2. İstenen kovanda Oluşturucular GUID'i altında bir kayıt defteri anahtarı oluşturun; burada GUID, belirli bir dilin proje sistemi veya [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hizmeti tarafından tanımlanan \\  GUID'tir.  Anahtarın adı, özel araç program adı olur. Özel araç anahtarı aşağıdaki değerlere sahiptir:

   - (Varsayılan)

        İsteğe bağlı. Özel aracın kullanıcı dostu bir açıklamasını sağlar. Bu parametre isteğe bağlıdır, ancak önerilir.

   - CLSID

        Gereklidir. uygulayan COM bileşeninin sınıf kitaplığının tanımlayıcısını <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> belirtir.

   - GeneratesDesignTimeSource

        Gereklidir. Bu özel araç tarafından üretilen dosya türlerinden gelen türlerin görsel tasarımcılar tarafından kullanılabilir olup olmadığını gösterir. Bu parametrenin değeri, görsel tasarımcılar tarafından kullanılabilir durumda olan türler için (sıfır) 0, görsel tasarımcılar tarafından kullanılabilen türler için ise (bir) 1 olmalıdır.

   > [!NOTE]
   > Özel aracın kullanılabilir olması istediğiniz her dil için özel aracı ayrı ayrı kaydetmelisiniz.

    Örneğin, MSDataSetGenerator her dil için kendisini bir kez kaydediyor:

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
- [BuildManager Nesnesine Giriş](/previous-versions/8f9kffa8(v=vs.140))