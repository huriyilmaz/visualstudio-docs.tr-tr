---
title: Interop Montaj Komut Amirleri Kayıt | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e2ab6389f1e0d369dd095290d12c97431c44155
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705857"
---
# <a name="registering-interop-assembly-command-handlers"></a>Birlikte Çalışma Bütünleştirilmiş Kodu Komut İşleyicilerini Kaydetme
Bir VSPackage, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamının (IDE) komutlarını düzgün bir şekilde yönlendirirse kaydolmalıdır.

 Kayıt defteri, el ile düzenleme veya Kayıt Şirketi (.rgs) dosyası kullanılarak güncellenebilir. Daha fazla bilgi için [Bkz. Kayıt Defteri Komut Dosyaları Oluşturma.](/cpp/atl/creating-registrar-scripts)

 Yönetilen Paket Çerçevesi (MPF) bu <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> işlevselliği sınıf boyunca sağlar.

- [Komut Tablosu Biçimi Başvuru](https://msdn.microsoft.com/library/09e9c6ef-9863-48de-9483-d45b7b7c798f) kaynakları yönetilmeyen uydu UI dlls bulunur.

## <a name="command-handler-registration-of-a-vspackage"></a>BIR VSPackage Komut Hander Kaydı
 Kullanıcı arabirimi (UI) tabanlı komutlar için işleyici olarak hareket eden bir VSPackage, VSPackage'dan `GUID`sonra isimlendirilmiş bir kayıt defteri girişi gerektirir. Bu kayıt defteri girişi, VSPackage'ın UI kaynak dosyasının konumunu ve bu dosyadaki menü kaynağını belirtir. Kayıt defteri girişinin kendisi, sürüm * \<>'nin* (örneğin 9.0) sürümü [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]olduğu HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\*\<Sürüm>* \Menus altında yer alır.

> [!NOTE]
> kabuk başharfe çevrildiğinde HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<Sürüm>* kök yolu alternatif bir kökle geçersiz kılınabilir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Kök yol hakkında daha fazla bilgi için Windows [Installer ile VSPackages Yükleme'ye](../../extensibility/internals/installing-vspackages-with-windows-installer.md)bakın.

### <a name="the-ctmenu-resource-registry-entry"></a>CTMENU Kaynak Kayıt Defteri Girişi
 Kayıt defteri girişinin yapısı:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> `GUID` ,{XXXXXX-XXXX-XXXX-XXXX-XXXXXX-XXXXXXXXX} şeklindeki VSPackage'dır.

 Kaynak Bilgi>virgülle ayrılmış üç öğeden oluşur. * \<* Bu öğeler sırayla:

 \<*Kaynak DLL*> \<Yolu, Menü \<Kaynak *Kimliği*>, Menü *Sürümü*>

 Aşağıdaki tabloda Kaynak \< *Bilgileri*> alanlarını açıklanmaktadır.

| Öğe | Açıklama |
|---------------------------| - |
| \<*Kaynak DLL Yolu*> | Bu, menü kaynağını içeren dll kaynağına giden tam yoldur veya bu boş bırakılır ve VSPackage'ın kaynağıDLL'nin kullanılacağını gösterir (VSPackage'ın kendisinin kayıtlı olduğu Paketler alt anahtarında belirtildiği gibi).<br /><br /> Bu alanı boş bırakmak adettir. |
| \<*Menü Kaynak Kimliği*> | Bu, VSPackage için `CTMENU` bir [.vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) dosyasından derlenen tüm UI öğelerini içeren kaynağın kaynak kimliğidir. |
| \<*Menü Sürümü*> | Bu, kaynak için sürüm olarak `CTMENU` kullanılan bir sayıdır. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]tüm `CTMENU` `CTMENU` kaynakların önbelleğiyle kaynağın içeriğini ortaya çıkarmak gerekip gerekmediğini belirlemek için bu değeri kullanır. Bir remerge devenv kurulum komutu çalıştırılarak tetiklenir.<br /><br /> Bu değer başlangıçta 1 olarak ayarlanmalıdır ve `CTMENU` kaynaktaki her değişiklikten sonra ve remerge oluşmadan önce artımlı. |

### <a name="example"></a>Örnek
 Aşağıda, birkaç kaynak girişi örneği verilmiştir:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Birlikte Çalışma Bütünleştirilmiş Kodları Kullanan Komutlar ve Menüler](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)
