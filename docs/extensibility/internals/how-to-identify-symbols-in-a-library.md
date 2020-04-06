---
title: 'Nasıl Yapılsın: Kütüphanedeki Sembolleri Tanımla | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1fe920fabd05a875b336467fbba16e4229fa9613
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708010"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Nasıl yapilir: Kitaplıktaki sembolleri tanımlama
Sembol tarama araçları sembollerin hiyerarşik görünümlerini görüntüler. Semboller ad alanlarını, nesneleri, sınıfları, sınıf üyelerini ve diğer dil öğelerini temsil eder.

 Hiyerarşideki her sembol, sembol kitaplığı tarafından aşağıdaki arabirimler [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aracılığıyla nesne yöneticisine aktarılan gezinti bilgileriyle tanımlanabilir:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.

 Hiyerarşideki sembolün konumu bir sembolü ayırt eder. Sembol tarama araçlarının belirli bir sembole gitmesini sağlar. Sembole giden benzersiz, tam nitelikli yol konumu belirler. Yoldaki her öğe bir düğümdür. Yol üst düzey düğümle başlar ve belirli bir sembolle biter. Örneğin, M1 yöntemi C1 sınıfının bir üyesiyse ve C1 N1 ad alanındaysa, M1 yönteminin tam yolu N1'dir. C1' e. M1' den. Bu yol üç düğüm içerir: N1, C1 ve M1.

 Gezinti bilgileri, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nesne yöneticisinin hiyerarşide seçilen sembolleri bulmasını, seçmesini ve saklamasını sağlar. Bir tarama aracından diğerine gezinmeyi sağlar. Projedeki sembollere göz atmak için Nesne Tarayıcısı'nı kullanırken, bir yönteme sağ tıklayabilir ve yöntemi arama grafiğinde görüntülemek için **Çağrı Tarayıcısı** aracını başlatabilirsiniz. **Object Browser** [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]

 İki form sembol konumunu açıklar. Kanonik form sembolün tam nitelikli yolunu temel adatır. Bu hiyerarşide sembol benzersiz bir konumunu temsil eder. Sembol tarama aracından bağımsızdır. Kanonik form bilgilerini elde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] etmek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> nesne yöneticisi yöntemi çağırır. Sunu formu, sembolün belirli bir sembol tarama aracı içindeki konumunu açıklar. Sembolün konumu, hiyerarşideki diğer sembollerin konumuna göredir. Belirli bir sembolün birkaç sunu yolu olabilir, ancak yalnızca bir kanonik yol olabilir. Örneğin, C1 sınıfı C2 sınıfından devralındıysa ve her iki sınıf da N1 ad alanındaysa, **Nesne Tarayıcısı** aşağıdaki hiyerarşik ağacı görüntüler:

```
N1
    C1
        Bases and Interfaces
            C2
    C2
        Bases and Interfaces
. . . . . . . . . . .

```

 Bu örnekte C2 sınıfının kanonik yolu N1 + C2'dir. C2'nin sunu yolu C1 ve "Bazlar ve Arayüzler" düğümlerini içerir: N1 + C1 + "Bazlar ve Arayüzler" + C2.

 Sunu formu bilgilerini almak için nesne <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> yöneticisi yöntemi çağırır.

## <a name="to-obtain-canonical-and-presentation-forms-information"></a>Kanonik ve sunum formları bilgileri elde etmek için

1. Yöntemi <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> uygulayın.

     Nesne yöneticisi, sembolün kanonik yolunda bulunan düğümlistesini almak için bu yöntemi çağırır.

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

2. Yöntemi <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> uygulayın.

     Nesne yöneticisi, sembolün sunu yolunda bulunan düğümlistesini almak için bu yöntemi çağırır.

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol tarama araçlarını destekleme](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Nasıl yapilir: Kitaplığı nesne yöneticisine kaydedin](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Nasıl verilir: Kitaplık tarafından sağlanan sembollerin listelerini nesne yöneticisine göster](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
