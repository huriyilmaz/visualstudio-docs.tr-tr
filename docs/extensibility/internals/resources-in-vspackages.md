---
title: VSPackages | Microsoft Docs
description: VSPackage'lara hangi tür yerelleştirilmiş kaynakların ekli olduğunu öğrenin. Kaynakları yerel uydu kullanıcı arabirimi DLL'lere veya yönetilen uydu DLL'lere de katıştırmanız gerekir.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 069ceef0275ce802a9f6bc717baee48a82a5df30e08dba1122f75ea429c2cac8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121337818"
---
# <a name="resources-in-vspackages"></a>VSPackage’lardaki Kaynaklar
Yerelleştirilmiş kaynakları yerel uydu kullanıcı arabirimi DLL'lerine, yönetilen uydu DLL'lerine veya yönetilen bir VSPackage'ın kendisine katıştırma.

 Bazı kaynaklar VSPackage'lara katıştıramaz. Aşağıdaki yönetilen türler ekli olabilir:

- Dizeler

- Paket yükleme anahtarları (aynı zamanda dizeler)

- Araç penceresi simgeleri

- Derlenmiş Komut Tablosu Çıktısı (CTO) dosyaları

- CTO bit eşlemleri

- Komut Satırı Yardımı

- İletişim kutusu verileri hakkında

  Yönetilen pakette yer alan kaynaklar kaynak kimliğine göre seçilir. Özel durum, CTO dosyasıdır ve bu dosya CTMENU olarak adlandırılmıştır. CTO dosyası kaynak tablosunda olarak görün `byte[]` gerekir. Diğer tüm kaynak öğeleri türe göre tanımlanır.

  Yönetilen kaynakların kullanılabilir <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> olduğunu belirtmek [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] için özniteliğini kullanabilirsiniz.

  :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdkresources/cs/vssdkresourcespackage.cs" id="Snippet1":::
  :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkresources/vb/vssdkresourcespackage.vb" id="Snippet1":::

  Bu şekilde ayar, örneğin kullanarak kaynakları ararken, unmanaged uydu URL'lerini <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yoksaymak gerektiğini <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A> gösterir. Aynı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaynak kimliğine sahip iki veya daha fazla kaynakla karşılaşırsa bulduğu ilk kaynağı kullanır.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir araç penceresi simgesinin yönetilen gösterimidir.

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

 Aşağıdaki örnek, CTO byte dizisinin nasıl eklenerek CTMENU olarak adlandırılmış olması gerektiğini gösterir.

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
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mümkün olduğunda VSPackage'ların yüklenmesini geciktirmektedir. VsPackage'a bir CTO dosyası eklemenin bir sonucu, Kurulum sırasında bu tür tüm VSPackage'ları belleğe yüklemesi gerekir. Bu, birleştirilmiş bir komut tablosu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] derlemesi sırasında olur. Kaynaklar VSPackage'da kod çalıştırmadan meta veriler inceler ve vsPackage'dan ayıklanır. VSPackage şu anda başlatılmamış olduğundan performans kaybı en düşük düzeydedir.

 Kurulumdan sonra VSPackage'dan bir kaynak isteğinde bulunduktan sonra bu paketin zaten yüklenmiş ve başlatılmış olması olasıdır, dolayısıyla [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] performans kaybı en düşük düzeydedir.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’ları Yönetme](../../extensibility/managing-vspackages.md)
- [MFC Uygulamalarında Yerelleştirilmiş Kaynaklar: Uydu DLL'leri](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)
