---
title: Tek dosya oluşturanlar kaydediliyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6afcd708ac50a46ceb3359f0d2c0821e3b788f47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696099"
---
# <a name="registering-single-file-generators"></a>Tek Dosya Oluşturucuları Kaydetme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Özel bir aracın ' de kullanılabilmesini sağlamak için [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , onu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] örneklendirilecek ve belirli bir proje türüyle ilişkilenbilmeniz için kaydetmeniz gerekir.  
  
### <a name="to-register-a-custom-tool"></a>Özel bir araç kaydetmek için  
  
1. Özel araç DLL 'sini [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] yerel kayıt defterinde veya sistem kayıt defterinde, HKEY_CLASSES_ROOT altına kaydedin.  
  
     Örneğin, aşağıda verilen yönetilen MSDataSetGenerator özel aracı için kayıt bilgileri verilmiştir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] :  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2. İstenen Hive içindeki bir kayıt defteri anahtarını [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] \\ , *GUID* 'in belirli dilin proje sistemi veya hizmeti tarafından tanımlanan GUID olduğu,*Bu GUID* 'nin altında yer aldığı bir kayıt defteri anahtarı oluşturun. Anahtarın adı, özel aracınıza ait programlı ad olur. Özel araç anahtarı aşağıdaki değerlere sahiptir:  
  
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
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{e6fdf8b0-f3d1-11d4-8576-0002a516ece8}\MSDataSetGenerator]  
    @="Microsoft J# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [Tek dosya oluşturucularını uygulama](../../extensibility/internals/implementing-single-file-generators.md)   
 [Projenin varsayılan ad alanını belirleme](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Türleri görsel tasarımcılara gösterme](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [BuildManager nesnesine giriş](https://msdn.microsoft.com/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
