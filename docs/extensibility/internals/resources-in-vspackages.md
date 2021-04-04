---
title: VSPackages 'teki kaynaklar | Microsoft Docs
description: Hangi tür yerelleştirilmiş kaynakların VSPackages 'e katıştırılabileceği hakkında bilgi edinin. Ayrıca yerel uydu UI dll 'Leri veya yönetilen uydu dll 'Lerine kaynak ekleyebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a80fc4fbfaf9a308492345ba897363d31d4669ca
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216546"
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

  Yönetilen paketteki kaynaklar kaynak KIMLIĞI tarafından seçilir. Özel durum, CTMENU adlı bir CTO dosyasıdır. CTO dosyası kaynak tablosunda bir olarak görünmelidir `byte[]` . Diğer tüm kaynak öğeleri türe göre tanımlanır.

  <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>Yönetilen kaynakların kullanılabilir olduğunu göstermek için özniteliğini kullanabilirsiniz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

  :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdkresources/cs/vssdkresourcespackage.cs" id="Snippet1":::
  :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkresources/vb/vssdkresourcespackage.vb" id="Snippet1":::

  <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>Bu şekilde ayarlanması [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , örneğin kullanarak, kaynakları ararken yönetilmeyen uydu dll 'lerini yoksayması gerektiğini belirtir <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A> . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Aynı kaynak kimliğine sahip iki veya daha fazla kaynakla karşılaşırsa, bulduğu ilk kaynağı kullanır.

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
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mümkün olduğunda VSPackages yükleme gecikmeleri. Bir VSPackage içindeki bir CTO dosyasını gömmenin bir sonucu, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Kurulum sırasında bir birleştirilmiş komut tablosu oluştururken bulunan tüm VSPackages 'leri belleğe yüklemelidir. Kaynak, VSPackage 'da kod çalıştırmadan meta verileri inceleyerek VSPackage 'dan ayıklanabilir. VSPackage Şu anda başlatılmaz, bu nedenle performans kaybı en düşük düzeydedir.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Kurulumdan sonra bir VSPackage kaynağından bir kaynak istediğinde, bu paketin daha önce yüklenmiş ve başlatılmış olması olasıdır, bu nedenle performans kaybı en düşük düzeydedir.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’ları Yönetme](../../extensibility/managing-vspackages.md)
- [MFC uygulamalarında yerelleştirilmiş kaynaklar: uydu dll 'Leri](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)
