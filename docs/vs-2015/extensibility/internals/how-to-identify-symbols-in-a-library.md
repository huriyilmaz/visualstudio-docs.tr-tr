---
title: 'Nasıl yapılır: kitaplıkta sembolleri belirleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f154c63940189f1a6035246fb7f72ec27be677f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191872"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Nasıl Yapılır: Bir Kitaplıktaki Sembolleri Tanımlama
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sembol tarama araçları, simgelerin hiyerarşik görünümlerini görüntüler. Semboller ad alanlarını, nesneleri, sınıfları, sınıf üyelerini ve diğer dil öğelerini temsil eder.  
  
 Hiyerarşideki her bir sembol, aşağıdaki arabirimler aracılığıyla sembol kitaplığı tarafından nesne yöneticisine geçirilen gezinti bilgileriyle tanımlanabilir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] :  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.  
  
 Hiyerarşide sembolün konumu bir sembolü ayırır. Sembol tarama araçlarının belirli bir simgeye gitmesini sağlar. Simgenin benzersiz ve tam yolu, konumu belirler. Yoldaki her öğe bir düğümdür. Yol, en üst düzey düğümle başlar ve belirli bir simgeyle biter. Örneğin, M1 yöntemi C1 sınıfının bir üyesi ise ve C1 N1 ad alanında ise, M1 yönteminin tam yolu N1 ' dir. =. M1. Bu yol üç düğüm içerir: N1, C1 ve M1.  
  
 Gezinti bilgileri, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nesne yöneticisinin hiyerarşide sembolleri bulmasını, seçmesini ve seçili halde tutmayı sağlar. Bir gözatma aracından diğerine gezinmeye izin verir. Bir projedeki simgelere gözatabilmeniz için **nesne tarayıcısı** kullanırken, yöntemi bir [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] çağrı grafiğinde göstermek için bir yönteme sağ tıklayıp **çağrı tarayıcısı** aracını başlatabilirsiniz.  
  
 Sembol konumunu iki form tanımlıyor. Kurallı form, simgenin tam yolunu temel alır. Hiyerarşide sembolün benzersiz bir konumunu temsil eder. Sembol tarama aracından bağımsızdır. Kurallı form bilgilerini elde etmek için, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nesne Yöneticisi yöntemini çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> . Sunum Formu, belirli bir sembol tarama aracı içindeki simgenin konumunu açıklar. Simgenin konumu, hiyerarşik içindeki diğer sembollerin konumlarına göre değişir. Verilen sembolün çeşitli sunum yolları olabilir, ancak yalnızca bir kurallı yol olabilir. Örneğin, C1 sınıfı C2 sınıfından devralınmışsa ve her iki sınıf de N1 ad alanında yer alıyorsa, **nesne tarayıcısı** aşağıdaki hiyerarşik ağacı görüntüler:  
  
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
  
## <a name="identifying-a-symbol-in-the-hierarchy"></a>Hiyerarşide sembol tanımlama  
  
#### <a name="to-obtain-canonical-and-presentation-forms-information"></a>Kurallı ve sunum formları bilgilerini elde etmek için  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sembol tarama araçlarını destekleme](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Nasıl yapılır: bir kitaplığı nesne yöneticisiyle kaydetme](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Nasıl Yapılır: Kitaplık Tarafından Sağlanan Sembollerin Listelerini Nesne Yöneticisine Sunma](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
