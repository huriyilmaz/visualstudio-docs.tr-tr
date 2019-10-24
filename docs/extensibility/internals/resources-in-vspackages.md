---
title: VSPackages 'teki kaynaklar | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07e1e19f802203b9770764330ea894b7d0eb98b8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724164"
---
# <a name="resources-in-vspackages"></a>VSPackage’lardaki Kaynaklar
Yerelleştirilmiş kaynakları yerel uydu UI dll 'Lerine, yönetilen uydu dll 'Lerine veya yönetilen bir VSPackage 'a ekleyebilirsiniz.

 Bazı kaynaklar VSPackages içine Katıştırılamaz. Aşağıdaki yönetilen türler gömülebilir:

- Dizeler

- Paket yükleme anahtarları (Ayrıca dizeler)

- Araç penceresi simgeleri

- Derlenen komut tablosu çıkışı (CTO) dosyaları

- CTO bit eşlemler

- Komut satırı yardımı

- İletişim kutusu verileri hakkında

  Yönetilen paketteki kaynaklar kaynak KIMLIĞI tarafından seçilir. Özel durum, CTMENU adlı bir CTO dosyasıdır. CTO dosyası kaynak tablosunda bir `byte[]` olarak görünmelidir. Diğer tüm kaynak öğeleri türe göre tanımlanır.

  Yönetilen kaynakların kullanılabilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] olduğunu göstermek için <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> özniteliğini kullanabilirsiniz.

  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]

  Bu şekilde <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> ayarlanması, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], örneğin <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A> kullanarak, kaynak ararken yönetilmeyen uydu dll 'Lerini yoksayması gerektiğini belirtir. @No__t_0 aynı kaynak KIMLIĞINE sahip iki veya daha fazla kaynakla karşılaşırsa, bulduğu ilk kaynağı kullanır.

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
 mümkün olduğunda VSPackages yükleme gecikmeleri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. CTO dosyasını VSPackage 'a gömmenin bir sonucu, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], birleştirilmiş bir komut tablosu oluşturduğunda, kurulum sırasında bellekte bulunan tüm VSPackages 'leri yüklemesi gerekir. Kaynak, VSPackage 'da kod çalıştırmadan meta verileri inceleyerek VSPackage 'dan ayıklanabilir. VSPackage Şu anda başlatılmaz, bu nedenle performans kaybı en düşük düzeydedir.

 @No__t_0 kurulumdan sonra bir VSPackage kaynağından bir kaynak istediğinde, bu paketin daha önce yüklenmiş ve başlatılmış olması, dolayısıyla performans kaybı en düşük olasılıktır.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’ları Yönetme](../../extensibility/managing-vspackages.md)
- [MFC Uygulamalarında Yerelleştirilmiş Kaynaklar: Uydu DLL'leri](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)
