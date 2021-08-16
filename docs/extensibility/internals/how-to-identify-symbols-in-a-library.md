---
title: 'Nasıl: Kitaplık Kitaplığında Sembolleri | Microsoft Docs'
description: Sembol kitaplığından nesne yöneticisine gezinti bilgilerini geçiren yöntemler kullanarak bir kitaplıkta sembolleri Visual Studio öğrenin.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d2b4d306203d90e7891aea4cfe97a034caa39dfbd279e8b93d65c2e8b39b5a62
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121376202"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Nasıllı: Kitaplıkta sembolleri tanımlama
Sembol tarama araçları sembollerin hiyerarşik görünümlerini görüntüler. Semboller ad alanlarını, nesneleri, sınıfları, sınıf üyelerini ve diğer dil öğelerini temsil eder.

 Hiyerarşide her simge, sembol kitaplığı tarafından nesne yöneticisine aşağıdaki arabirimler aracılığıyla [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geçirilen gezinti bilgileriyle belirlenebilirsiniz:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.

 Hiyerarşide sembolün konumu bir simgeyi ayırt eder. Sembol tarama araçlarının belirli bir sembole gezinmesi için izin verir. Simgenin benzersiz, tam yolu konumu belirler. Yoldeki her öğe bir düğüm olur. Yol üst düzey düğümle başlar ve belirli bir simgeyle biter. Örneğin, M1 yöntemi C1 sınıfının bir üyesi ise ve C1 N1 ad alanı ise, M1 yönteminin tam yolu N1'tir. C1. M1. Bu yol üç düğüm içerir: N1, C1 ve M1.

 Gezinti bilgileri, nesne [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yöneticisinin hiyerarşide sembolleri bulmasını, seçmesini ve seçmesini sağlar. Bir gözatma aracından diğerine gezinmeye olanak sağlar. Bir proje **içinde sembollere** göz atmak için Object Browser'ı kullanırken, bir yönteme sağ tıklayabilirsiniz ve Çağrı Tarayıcısı aracını başlatarak [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] yöntemi bir çağrı grafiğinde  görüntüleyebilirsiniz.

 İki form sembol konumunu açıklar. Kurallı form, sembolün tam yolunu temel alan bir formdur. Hiyerarşide sembolün benzersiz konumunu temsil eder. Sembol tarama aracında bağımsızdır. Kurallı form bilgilerini almak için nesne [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yöneticisi yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> arar. Sunu formu, sembolün belirli bir sembol tarama aracı içindeki konumunu açıklar. Sembolün konumu, hiyerarşide diğer sembollerin konumuyla görelidir. Verilen bir simgenin birden fazla sunu yolu olabilir, ancak yalnızca bir kurallı yol vardır. Örneğin, C1 sınıfı C2 sınıfından devralınır ve her iki sınıf da N1 ad alanına sahipse **Object Browser** aşağıdaki hiyerarşik ağacı görüntüler:

```
N1
    C1
        Bases and Interfaces
            C2
    C2
        Bases and Interfaces
. . . . . . . . . . .

```

 Bu örnekte C2 sınıfının kurallı yolu N1 + C2'dir. C2'nin sunu yolu C1 ve "Temeller ve Arabirimler" düğümlerini içerir: N1 + C1 + "Temeller ve Arabirimler" + C2.

 Sunu formu bilgilerini almak için nesne yöneticisi yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> çağırtır.

## <a name="to-obtain-canonical-and-presentation-forms-information"></a>Kurallı ve sunum formları bilgilerini almak için

1. yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> uygulama.

     Nesne yöneticisi, sembolün kurallı yolunda bulunan düğümlerin listesini almak için bu yöntemi arar.

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

2. yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> uygulama.

     Nesne yöneticisi, sembolün sunu yolunda yer alan düğümlerin listesini almak için bu yöntemi arar.

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol tarama araçlarını destekleme](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Nasıl kullanılır: Nesne yöneticisine kitaplık kaydetme](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Nasıl kullanılır: Kitaplık tarafından sağlanan sembollerin listelerini nesne yöneticisine açığa çıkarma](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
