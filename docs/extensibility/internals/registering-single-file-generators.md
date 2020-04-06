---
title: Tek Dosya Jeneratörleri Kayıt | Microsoft Dokümanlar
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
ms.openlocfilehash: 1cea2ebba4739695393447a36e9842ade1670954
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705807"
---
# <a name="registering-single-file-generators"></a>Tek Dosya Oluşturucuları Kaydetme
Özel bir aracı kullanılabilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]hale getirmek için, bu aracı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] anında kaydedebilirsiniz ve belirli bir proje türüyle ilişkilendirmek için kaydetmeniz gerekir.

### <a name="to-register-a-custom-tool"></a>Özel bir aracı kaydetmek için

1. Özel araç DLL'yi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yerel kayıt defterine veya sistem kayıt defterine HKEY_CLASSES_ROOT altında kaydedin.

    Örneğin, burada yönetilen MSDataSetGenerator özel aracı için kayıt bilgileri, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]hangi ile birlikte gelir:

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]
   @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"
   "ThreadingModel"="Both"
   "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"
   ```

2. GUID belirli bir dilin [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proje sistemi\\veya hizmeti tarafından tanımlanan *GUID* olduğu Jeneratörler*GUID* altında istenilen kovan bir kayıt defteri anahtarı oluşturun. Anahtarın adı, özel aracınızın programatik adı olur. Özel araç anahtarı aşağıdaki değerlere sahiptir:

   - (Varsayılan)

        İsteğe bağlı. Özel aracın kullanıcı dostu bir açıklamasını sağlar. Bu parametre isteğe bağlıdır, ancak önerilir.

   - Clsıd

        Gereklidir. Uygulayan COM bileşeninin sınıf kitaplığı tanımlayıcısını <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>belirtir.

   - OluştururDesignTimeSource

        Gereklidir. Bu özel araç tarafından üretilen dosyalardan türlerin görsel tasarımcıların kullanımına sunulup sunulmadığını gösterir. Bu parametrenin değerinin görsel tasarımcılar tarafından kullanılamayan türler için (sıfır) 0 veya görsel tasarımcılar için kullanılabilen türler için (bir) 1 olması gerekir.

   > [!NOTE]
   > Özel aracın kullanılabilir olmasını istediğiniz her dil için özel aracı ayrı ayrı kaydetmeniz gerekir.

    Örneğin, MSDataSetGenerator her dil için bir kez kendini kaydeder:

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
- [BuildManager Nesnesine Giriş](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
