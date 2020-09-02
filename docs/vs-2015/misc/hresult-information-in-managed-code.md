---
title: Yönetilen koddaki HRESULT bilgileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, HRESULT information
- HRESULT, managed VSPackages
ms.assetid: 0795ee94-17a8-4327-bf57-27cd5e312a4c
caps.latest.revision: 29
manager: jillfra
ms.openlocfilehash: 4f80b575656c2d8b1740f217f2e144f89f254078
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681627"
---
# <a name="hresult-information-in-managed-code"></a>Yönetilen koddaki HRESULT bilgileri
Yönetilen kod ve COM arasındaki etkileşim, HRESULT dönüş değerleriyle karşılaşıldığında sorunlara neden olabilir.  
  
 Bir COM arabiriminde, HRESULT dönüş değeri şu rolleri yürütebilir:  
  
- Hata bilgilerini sunun (örneğin, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> ).  
  
- Normal program davranışına ilişkin durum bilgilerini sunun.  
  
  COM yönetilen koda çağırdığında, HRESULTs bu sorunlara neden olabilir:  
  
- Sıfırdan küçük HRESULT değerleri döndüren COM işlevleri (hata kodları) özel durum oluşturur.  
  
- Veya gibi iki veya daha fazla farklı başarı kodunu düzenli olarak döndüren COM yöntemleri <xref:Microsoft.VisualStudio.VSConstants.S_OK> ayırt edilemez <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> .  
  
  [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]Com işlevlerinin birçoğu sıfırdan küçük HRESULT değerleri döndürdüğü veya farklı başarı kodları döndürtiğinden, [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] birlikte çalışma derlemeleri, yöntem imzalarının korunması için yazılmıştır. Tüm [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] birlikte çalışma yöntemleri `int` türdür. HRESULT değerleri, değişiklik yapılmadan ve özel durum oluşturmadan birlikte çalışma katmanından geçirilir.  
  
  Bir COM işlevi çağıran yönetilen metoda bir HRESULT döndürdüğünden, çağıran yöntem HRESULT 'yi denetlemesi ve gerektiğinde özel durumlar oluşturması gerekir.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>COM 'dan yönetilen koda döndürülen HRESULTs işleme  
 Yönetilen koddan bir COM arabirimini çağırdığınızda, HRESULT değerini inceleyin ve gerekirse bir özel durum oluşturun. <xref:Microsoft.VisualStudio.ErrorHandler>Sınıfı, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> kendısıne geçirilen HRESULT değerine bağlı olarak bir com özel durumu oluşturan yöntemini içerir.  
  
 Varsayılan olarak, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> sıfırdan küçük bir değere sahip BIR HRESULT geçirildiğinde bir özel durum oluşturur. Bu tür Hsonuçların kabul edilebilir değerler olduğu ve hiçbir özel durum oluşturulması gereken durumlarda, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> değerler test edildikten sonra ek HSONUÇLARıN değerlerinin geçirilmesi gerekir. Test edilmekte olan HRESULT, açıkça geçirilen herhangi bir HRESULT değeri ile eşleşiyorsa <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> , hiçbir özel durum oluşturulmaz.  
  
> [!NOTE]
> Sınıfı, ve gibi <xref:Microsoft.VisualStudio.VSConstants> ortak HRESULTS için sabitler içerir, örneğin, ve <xref:Microsoft.VisualStudio.VSConstants.S_OK> <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT> . <xref:Microsoft.VisualStudio.VSConstants> Ayrıca, <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> com 'daki başarılı ve başarısız makrolara karşılık gelen ve yöntemlerini de sağlar.  
  
 Örneğin, <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> kabul edilebilir bir dönüş değeri olan, ancak sıfırdan küçük DIĞER HRESULT bir hatayı temsil eden aşağıdaki işlev çağrısını göz önünde bulundurun.  
  
 [!code-csharp[VSSDKHRESULTInformation#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#1)]
 [!code-vb[VSSDKHRESULTInformation#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#1)]  
  
 Birden fazla kabul edilebilir dönüş değeri varsa, ek HRESULT değerleri yalnızca öğesine yapılan çağrının listesine eklenebilir <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> .  
  
 [!code-csharp[VSSDKHRESULTInformation#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#2)]
 [!code-vb[VSSDKHRESULTInformation#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#2)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>Yönetilen koddan COM 'a HRESULTS döndürme  
 Özel durum oluşursa, yönetilen kod <xref:Microsoft.VisualStudio.VSConstants.S_OK> onu ÇAĞıRAN com işlevine geri döner. COM birlikte çalışması, yönetilen kodda kesin olarak belirlenmiş ortak özel durumları destekler. Örneğin, kabul edilemez bir bağımsız değişken alan bir yöntem `null` bir oluşturur <xref:System.ArgumentNullException> .  
  
 Hangi özel durumun oluşturulması gerektiğini, ancak COM 'a geri dönmek istediğiniz HRESULT 'yi biliyorsanız, <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> uygun bir özel durum oluşturmak için yöntemini kullanabilirsiniz. Bu, standart dışı bir hata ile (örneğin,) birlikte kullanılır <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> . <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> kendisine geçirilen HRESULT 'yi kesin türü belirtilmiş bir özel durumla eşlemeye çalışır. Değilse, bunun yerine genel bir COM özel durumu oluşturur. Nihai sonuç, <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> yönetilen koddan kendisine GEÇIRDIĞINIZ HRESULT, ÇAĞıRAN com işlevine döndürülür.  
  
> [!NOTE]
> Özel durumların performansı tehlikeye alınır ve anormal program koşullarını göstermek için tasarlanmıştır. Genellikle oluşan koşulların, oluşturulan özel durum yerine satır içi olarak işlenmesi gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen VSPackages](../misc/managed-vspackages.md)   
 [Yönetilmeyen kodla birlikte çalışma](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)   
 [Nasıl yapılır: HRESULTs ve özel durumları eşleme](https://msdn.microsoft.com/library/610b364b-2761-429d-9c4a-afbc3e66f1b9)   
 [Birlikte çalışabilirlik için COM bileşenleri oluşturma](https://msdn.microsoft.com/7a2c657a-cfef-40f0-bed3-7c2c0ac4abdf)   
 [Yönetilen VSPackages](../misc/managed-vspackages.md)