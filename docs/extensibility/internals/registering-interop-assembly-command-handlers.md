---
title: Birlikte çalışma bütünleştirilmiş kodu komut Işleyicilerini kaydetme | Microsoft Docs
description: Birlikte çalışma derlemelerini kullanarak tüm VSPackages uygulama komutları tarafından kullanılan temel komut sözleşmesi hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b45fe06722b190569e067dccd325ba4acac4fb0f
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875178"
---
# <a name="registering-interop-assembly-command-handlers"></a>Birlikte Çalışma Bütünleştirilmiş Kodu Komut İşleyicilerini Kaydetme
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Tümleşik geliştirme ortamı (IDE) komutlarının düzgün şekilde yönlendirildiği için bir VSPackage ile kaydolmalıdır.

 Kayıt defteri el ile düzenlemeyle veya bir kaydedici (. RGS) dosyası kullanılarak güncelleştirilebilen olabilir. Daha fazla bilgi için bkz. [kaydedici betikleri oluşturma](/cpp/atl/creating-registrar-scripts).

 Yönetilen paket çerçevesi (MPF), sınıfı aracılığıyla bu işlevselliği sağlar <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> .

- [Komut tablosu biçimi başvuru](/previous-versions/bb164647(v=vs.100)) kaynakları, YÖNETILMEYEN uydu UI dll 'lerinde bulunur.

## <a name="command-handler-registration-of-a-vspackage"></a>VSPackage komut Işleyicisi kaydı
 Kullanıcı arabirimi (UI) tabanlı komutlar için işleyici olarak davranan bir VSPackage, VSPackage 'tan sonra adlı bir kayıt defteri girişi gerektirir `GUID` . Bu kayıt defteri girdisi, VSPackage 'un Kullanıcı arabirimi kaynak dosyasının ve bu dosya içindeki menü kaynağının konumunu belirtir. Kayıt defteri girişinin kendisi HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ *\<Version>* \Menus altında bulunur *\<Version>* [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . örneğin, sürümü, 9,0.

> [!NOTE]
> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudiokök yolu, \\ *\<Version>* kabuk başlatıldığında alternatif bir kökle geçersiz kılınabilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Kök yolu hakkında daha fazla bilgi için, [Windows Installer Ile VSPackages yükleme](../../extensibility/internals/installing-vspackages-with-windows-installer.md)bölümüne bakın.

### <a name="the-ctmenu-resource-registry-entry"></a>CTMENU kaynak kayıt defteri girdisi
 Kayıt defteri girişinin yapısı:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> , `GUID` VSPackage öğesinin {xxxxxx-xxxx-xxxx-xxxx-XXXXXXXXX} biçiminde olur.

 *\<Resource Information>* virgülle ayrılmış üç öğeden oluşur. Bu öğeler sırasıyla:

 \<*Path to Resource DLL*>, \<*Menu Resource ID*>, \<*Menu Version*>

 Aşağıdaki tabloda, alanları açıklanmaktadır \<*Resource Information*> .

| Öğe | Açıklama |
|---------------------------| - |
| \<*Path to Resource DLL*> | Bu, menü kaynağını içeren kaynak DLL 'inin tam yoludur veya boş bırakılır. Bu, VSPackage 'un kaynak DLL 'sinin, VSPackage 'un kaydedildiği paket alt anahtarında belirtildiği gibi) kullanılacağını gösterir.<br /><br /> Bu alanı boş bırakmak önemlidir. |
| \<*Menu Resource ID*> | Bu, `CTMENU` bir [. vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) dosyasından derlenen VSPackage IÇIN tüm Kullanıcı arabirimi öğelerini IÇEREN kaynağın kaynak kimliğidir. |
| \<*Menu Version*> | Bu, kaynağın sürümü olarak kullanılan bir sayıdır `CTMENU` . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Bu değeri, `CTMENU` kaynağın içeriğini tüm kaynakların önbelleğine yeniden birleştirmenin gerekip gerekmediğini öğrenmek için kullanır `CTMENU` . Yeniden birleştirme, devenv Kurulum komutu çalıştırılarak tetiklenir.<br /><br /> Başlangıçta bu değer 1 ' e ayarlanmalıdır ve kaynaktaki her değişiklikten sonra `CTMENU` yeniden birleştirme gerçekleşmeden önce arttırılır. |

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