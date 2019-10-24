---
title: Birlikte çalışma bütünleştirilmiş kodu komut Işleyicilerini kaydetme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbc0d162a11df034bec4d1f357ef8abd106da401
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724698"
---
# <a name="registering-interop-assembly-command-handlers"></a>Birlikte Çalışma Bütünleştirilmiş Kodu Komut İşleyicilerini Kaydetme
Tümleşik geliştirme ortamı (IDE), komutlarının düzgün şekilde yönlendirilebilmesi için bir VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaydedilmelidir.

 Kayıt defteri el ile düzenlemeyle veya bir kaydedici (. RGS) dosyası kullanılarak güncelleştirilebilen olabilir. Daha fazla bilgi için bkz. [kaydedici betikleri oluşturma](/cpp/atl/creating-registrar-scripts).

 Yönetilen paket çerçevesi (MPF), bu işlevselliği <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> sınıfı aracılığıyla sağlar.

- [Komut tablosu biçimi başvuru](https://msdn.microsoft.com/library/09e9c6ef-9863-48de-9483-d45b7b7c798f) kaynakları, YÖNETILMEYEN uydu UI dll 'lerinde bulunur.

## <a name="command-handler-registration-of-a-vspackage"></a>VSPackage komut Işleyicisi kaydı
 Kullanıcı arabirimi (UI) tabanlı komutlar için işleyici olarak davranan bir VSPackage, VSPackage `GUID` sonra adlı bir kayıt defteri girişi gerektirir. Bu kayıt defteri girdisi, VSPackage 'un Kullanıcı arabirimi kaynak dosyasının ve bu dosya içindeki menü kaynağının konumunu belirtir. Kayıt defteri girişinin kendisi HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio \\ *\<Version >* \menülerinin altında bulunur, burada *\<Version >* [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sürümüdür, örneğin 9,0.

> [!NOTE]
> @No__t_3 kabuğu başlatıldığında, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio \\ *\<Version >* kök yolu alternatif bir kökle geçersiz kılınabilir. Kök yolu hakkında daha fazla bilgi için, [Windows Installer Ile VSPackages yükleme](../../extensibility/internals/installing-vspackages-with-windows-installer.md)bölümüne bakın.

### <a name="the-ctmenu-resource-registry-entry"></a>CTMENU kaynak kayıt defteri girdisi
 Kayıt defteri girişinin yapısı:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*guıd*>, {xxxxxx-XXXX-XXXX-XXXX-xxxxxxxxx} biçiminde VSPackage 'ın `GUID`.

 *\<Resource bilgi >* , virgülle ayrılmış üç öğeden oluşur. Bu öğeler sırasıyla:

 *kaynak DLL > yolu*\< \<*menü kaynak kimliği*>, \<*Menu sürümü* >

 Aşağıdaki tabloda > \<*kaynak bilgileri*alanları açıklanmaktadır.

| Öğe | Açıklama |
|---------------------------| - |
| *kaynak dll 'Nin yolunu* \< > | Bu, menü kaynağını içeren kaynak DLL 'inin tam yoludur veya boş bırakılır. Bu, VSPackage 'un kaynak DLL 'sinin, VSPackage 'un kaydedildiği paket alt anahtarında belirtildiği gibi) kullanılacağını gösterir.<br /><br /> Bu alanı boş bırakmak önemlidir. |
| \<*menü kaynak kimliği* > | Bu, bir [. vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) dosyasından derlenen VSPackage için tüm Kullanıcı arabirimi öğelerini içeren `CTMENU` KAYNAĞıNıN kaynak kimliğidir. |
| \<*menü sürümü* > | Bu, `CTMENU` kaynağın sürümü olarak kullanılan bir sayıdır. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], `CTMENU` kaynağın içeriğini tüm `CTMENU` kaynakları önbelleğiyle yeniden birleştirmesi gerekip gerekmediğini öğrenmek için bu değeri kullanır. Yeniden birleştirme, devenv Kurulum komutu çalıştırılarak tetiklenir.<br /><br /> Bu değer başlangıçta 1 olarak ayarlanmalıdır ve `CTMENU` kaynaktaki her değişiklikten sonra yeniden birleştirme gerçekleşmeden önce arttırılır. |

### <a name="example"></a>Örnek
 Aşağıda birkaç kaynak girişi örneği verilmiştir:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Birlikte Çalışma Bütünleştirilmiş Kodları Kullanan Komutlar ve Menüler](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)