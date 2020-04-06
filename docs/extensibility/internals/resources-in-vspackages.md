---
title: VSPackages'taki Kaynaklar | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 493e9834e3d7cf6d82cebb8dd93d5369678c7be0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705598"
---
# <a name="resources-in-vspackages"></a>VSPackage’lardaki Kaynaklar
Yerelleştirilmiş kaynakları yerel uydu UI DL'lerine, yönetilen uydu DL'lerine veya yönetilen bir VSPackage'a katıştırabilirsiniz.

 Bazı kaynaklar VSPackages'e katışdırılamaz. Aşağıdaki yönetilen türleri katıştırılmış olabilir:

- Dizeler

- Paket yük anahtarları (aynı zamanda dizeleri olan)

- Araç penceresi simgeleri

- Derlenmiş Komut Tablosu Çıktısı (CTO) dosyaları

- CTO bit eşlemleri

- Komut Satırı Yardım

- İletişim kutusu verileri hakkında

  Yönetilen paketteki kaynaklar kaynak kimliğiyle seçilir. Özel durum, CTMENU olarak adlandırılması gereken CTO dosyasıdır. CTO dosyası kaynak tablosunda bir `byte[]`. Diğer tüm kaynak öğeleri türüne göre tanımlanır.

  Yönetilen kaynakların <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> kullanılabilir olduğunu belirtmek [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] için özniteliği kullanabilirsiniz.

  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]

  Bu <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> şekilde ayarlayarak, örneğin kaynakları ararken yönetilmeyen uydu DL'lerini göz ardı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] etmesi gerektiğini <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>gösterir. Aynı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaynak kimliğine sahip iki veya daha fazla kaynakla karşılaşırsa, bulduğu ilk kaynağı kullanır.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir araç penceresi simgesinin yönetilen bir temsilidir.

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

 Aşağıdaki örnek, CTMENU adı verilmesi gereken CTO bayt dizininin nasıl gömüleceğini gösterir.

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

## <a name="implementation-notes"></a>Uygulama Notları
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]mümkün olduğunda VSPackages'ın yüklenmesigeciktirir. Bir VSPackage'a bir CTO dosyası yerleştirmenin bir sonucu, birleştirilmiş bir komut tablosu oluşturduğunda Kurulum sırasında tüm bu VSPackages'ı belleğe yüklemesi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gerekir. Kaynaklar, VSPackage'da kod çalıştırmadan meta verileri inceleyerek VSPackage'dan çıkarılabilir. VSPackage şu anda başharfe fişlenmemişolduğundan, performans kaybı en az düzeydedir.

 Kurulumdan sonra bir VSPackage'dan kaynak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] istediğinde, bu paketin zaten yüklenmiş ve başolarak başlatılması olasıdır, bu nedenle performans kaybı en az düzeydedir.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’ları Yönetme](../../extensibility/managing-vspackages.md)
- [MFC Uygulamalarında Yerelleştirilmiş Kaynaklar: Uydu DLL'leri](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)
