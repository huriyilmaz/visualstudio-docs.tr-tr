---
title: VSPackages 'teki kaynaklar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 90674d17cdc3fb8956fd6eedeb3acb27226620cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696084"
---
# <a name="resources-in-vspackages"></a>VSPackage’lardaki Kaynaklar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Yerelleştirilmiş kaynakları yerel uydu UI dll 'Lerine, yönetilen uydu dll 'Lerine veya yönetilen bir VSPackage 'a ekleyebilirsiniz.  
  
 Bazı kaynaklar VSPackages içine Katıştırılamaz. Aşağıdaki yönetilen türler gömülebilir:  
  
- Dizeler  
  
- Paket yükleme anahtarları (Ayrıca dizeler)  
  
- Araç penceresi simgeleri  
  
- Derlenen komut tablosu çıkışı (CTO) dosyaları  
  
- CTO bit eşlemler  
  
- Komut satırı yardımı  
  
- İletişim kutusu verileri hakkında  
  
  Yönetilen paketteki kaynaklar kaynak KIMLIĞI tarafından seçilir. Özel durum, CTMENU adlı bir CTO dosyasıdır. CTO dosyası kaynak tablosunda bir olarak görünmelidir `byte[]` . Diğer tüm kaynak öğeleri türe göre tanımlanır.  
  
  <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>Yönetilen kaynakların kullanılabilir olduğunu göstermek için özniteliğini kullanabilirsiniz [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
  [!code-csharp[VSSDKResources#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdkresources/cs/vssdkresourcespackage.cs#1)]
  [!code-vb[VSSDKResources#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkresources/vb/vssdkresourcespackage.vb#1)]  
  
  <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>Bu şekilde ayarlanması [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , örneğin kullanarak, kaynakları ararken yönetilmeyen uydu dll 'lerini yoksayması gerektiğini belirtir <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A> . [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Aynı kaynak kimliğine sahip iki veya daha fazla kaynakla karşılaşırsa, bulduğu ilk kaynağı kullanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir araç penceresi simgesinin yönetilen bir gösterimidir.  
  
```  
<data name="1001"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyToolWinIcon.bmp;  
     System.Drawing.Bitmap,  
     System.Drawing,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
 Aşağıdaki örnek, CTMENU 'nin adlandırılması gereken CTO bayt dizisinin nasıl ekleneceğini gösterir.  
  
```  
<data name="CTMENU"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyPackage.cto;  
     System.Byte[],  
     mscorlib,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
## <a name="implementation-notes"></a>Uygulama notları  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mümkün olduğunda VSPackages yükleme gecikmeleri. Bir VSPackage içindeki bir CTO dosyasını gömmenin bir sonucu, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Kurulum sırasında bir birleştirilmiş komut tablosu oluştururken bulunan tüm VSPackages 'leri belleğe yüklemelidir. Kaynak, VSPackage 'da kod çalıştırmadan meta verileri inceleyerek VSPackage 'dan ayıklanabilir. VSPackage Şu anda başlatılmaz, bu nedenle performans kaybı en düşük düzeydedir.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Kurulumdan sonra bir VSPackage kaynağından bir kaynak istediğinde, bu paketin daha önce yüklenmiş ve başlatılmış olması olasıdır, bu nedenle performans kaybı en düşük düzeydedir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen VSPackages](../../misc/managed-vspackages.md)   
 [VSPackages 'yi yönetme](../../extensibility/managing-vspackages.md)   
 [MFC uygulamalarında yerelleştirilmiş kaynaklar: uydu dll 'Leri](https://msdn.microsoft.com/library/3a1100ae-a9c8-47b5-adbd-cbedef5992ef)   
 [Yönetilen VSPackages](../../misc/managed-vspackages.md)
