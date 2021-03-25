---
title: 'Nasıl yapılır: kitaplıkta sembolleri belirleme | Microsoft Docs'
description: Sembol kitaplığından Visual Studio nesne Yöneticisi 'ne gezinti bilgilerini geçiren yöntemler uygulayarak kitaplıktaki sembolleri nasıl tanımlayacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c6c897801b98857f4a310323d4e00583c98245d5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078883"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Nasıl yapılır: kitaplıkta sembolleri belirleme
Sembol tarama araçları, simgelerin hiyerarşik görünümlerini görüntüler. Semboller ad alanlarını, nesneleri, sınıfları, sınıf üyelerini ve diğer dil öğelerini temsil eder.

 Hiyerarşideki her bir sembol, aşağıdaki arabirimler aracılığıyla sembol kitaplığı tarafından nesne yöneticisine geçirilen gezinti bilgileriyle tanımlanabilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] :

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.

 Hiyerarşide sembolün konumu bir sembolü ayırır. Sembol tarama araçlarının belirli bir simgeye gitmesini sağlar. Simgenin benzersiz ve tam yolu, konumu belirler. Yoldaki her öğe bir düğümdür. Yol, en üst düzey düğümle başlar ve belirli bir simgeyle biter. Örneğin, M1 yöntemi C1 sınıfının bir üyesi ise ve C1 N1 ad alanında ise, M1 yönteminin tam yolu N1 ' dir. =. M1. Bu yol üç düğüm içerir: N1, C1 ve M1.

 Gezinti bilgileri, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nesne yöneticisinin hiyerarşide sembolleri bulmasını, seçmesini ve seçili halde tutmayı sağlar. Bir gözatma aracından diğerine gezinmeye izin verir. Bir projedeki simgelere gözatabilmeniz için **nesne tarayıcısı** kullanırken, yöntemi bir [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] çağrı grafiğinde göstermek için bir yönteme sağ tıklayıp **çağrı tarayıcısı** aracını başlatabilirsiniz.

 Sembol konumunu iki form tanımlıyor. Kurallı form, simgenin tam yolunu temel alır. Hiyerarşide sembolün benzersiz bir konumunu temsil eder. Sembol tarama aracından bağımsızdır. Kurallı form bilgilerini elde etmek için, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nesne Yöneticisi yöntemini çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> . Sunum Formu, belirli bir sembol tarama aracı içindeki simgenin konumunu açıklar. Simgenin konumu, hiyerarşideki diğer sembollerin konumuna göre değişir. Verilen sembolün çeşitli sunum yolları olabilir, ancak yalnızca bir kurallı yol olabilir. Örneğin, C1 sınıfı C2 sınıfından devralınmışsa ve her iki sınıf de N1 ad alanında yer alıyorsa, **nesne tarayıcısı** aşağıdaki hiyerarşik ağacı görüntüler:

```
N1
    C1
        Bases and Interfaces
            C2
    C2
        Bases and Interfaces
. . . . . . . . . . .

```

 Bu örnekte, C2 sınıfının kurallı yolu N1 + C2 ' dir. C2 sunum yolu C1 ve "temeller ve arabirimler" düğümleri içerir: N1 + C1 + "temeller ve arabirimler" + C2.

 Sunum formu bilgilerini almak için, nesne Yöneticisi <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> yöntemini çağırır.

## <a name="to-obtain-canonical-and-presentation-forms-information"></a>Kurallı ve sunum formları bilgilerini elde etmek için

1. Yöntemini uygulayın <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> .

     Nesne Yöneticisi, simgenin kurallı yolunda yer alan düğümlerin listesini almak için bu yöntemi çağırır.

    ```vb
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)
        Return 0
    End Function
    ```

    ```csharp
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)
    {
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =
            new CallBrowserEnumNavInfoNodes(m_strMethod);
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);
        return 0;
    }

    ```

2. Yöntemini uygulayın <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> .

     Nesne Yöneticisi, simgenin sunum yolunda yer alan düğümlerin listesini almak için bu yöntemi çağırır.

## <a name="see-also"></a>Ayrıca bkz.
- [Destek sembolü-tarama araçları](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Nasıl yapılır: bir kitaplığı nesne yöneticisiyle kaydetme](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Nasıl yapılır: kitaplık tarafından nesne yöneticisine sunulan simgelerin listesini kullanıma sunma](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
