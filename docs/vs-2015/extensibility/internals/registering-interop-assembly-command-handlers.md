---
title: Birlikte çalışma bütünleştirilmiş kodu komut Işleyicilerini kaydetme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9d2822e9eef36806f5c251813925fb4244242519
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705808"
---
# <a name="registering-interop-assembly-command-handlers"></a>Birlikte Çalışma Bütünleştirilmiş Kodu Komut İşleyicilerini Kaydetme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Tümleşik geliştirme ortamı (IDE) komutlarının düzgün şekilde yönlendirildiği için bir VSPackage ile kaydolmalıdır.  
  
 Kayıt defteri el ile düzenlemeyle veya bir kaydedici (. RGS) dosyası kullanılarak güncelleştirilebilen olabilir. Daha fazla bilgi için bkz. [kaydedici betikleri oluşturma](https://msdn.microsoft.com/library/cbd5024b-8061-4a71-be65-7fee90374a35).  
  
 Yönetilen paket çerçevesi (MPF), sınıfı aracılığıyla bu işlevselliği sağlar <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> .  
  
 [Komut tablosu biçimi başvuru](https://msdn.microsoft.com/09e9c6ef-9863-48de-9483-d45b7b7c798f) kaynakları, YÖNETILMEYEN uydu UI dll 'lerinde bulunur.  
  
## <a name="command-handler-registration-of-a-vspackage"></a>VSPackage komut Işleyicisi kaydı  
 Kullanıcı arabirimi (UI) tabanlı komutlar için işleyici olarak davranan bir VSPackage, VSPackage 'tan sonra adlı bir kayıt defteri girişi gerektirir `GUID` . Bu kayıt defteri girdisi, VSPackage 'un Kullanıcı arabirimi kaynak dosyasının ve bu dosya içindeki menü kaynağının konumunu belirtir. Kayıt defteri girişinin kendisi HKEY_LOCAL_MACHINE \Software\Microsoft\VisualStudio \\ *\<Version>* \Menus altında bulunur *\<Version>* [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . örneğin, sürümü, 9,0.  
  
> [!NOTE]
> HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio 'ın kök yolu, \\ *\<Version>* kabuk başlatıldığında alternatif bir kökle geçersiz kılınabilir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Kök yolu hakkında daha fazla bilgi için, [Windows Installer Ile VSPackages yükleme](../../extensibility/internals/installing-vspackages-with-windows-installer.md)bölümüne bakın.  
  
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
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|\<*Path to Resource DLL*>|Bu, menü kaynağını içeren kaynak DLL 'inin tam yoludur veya boş bırakılır. Bu, VSPackage 'un kaynak DLL 'sinin, VSPackage 'un kaydedildiği paket alt anahtarında belirtildiği gibi) kullanılacağını gösterir.<br /><br /> Bu alanı boş bırakmak önemlidir.|  
|\<*Menu Resource ID*>|Bu, `CTMENU` bir [. vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) dosyasından derlenen VSPackage IÇIN tüm Kullanıcı arabirimi öğelerini IÇEREN kaynağın kaynak kimliğidir.|  
|\<*Menu Version*>|Bu, kaynağın sürümü olarak kullanılan bir sayıdır `CTMENU` . [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Bu değeri, `CTMENU` kaynağın içeriğini tüm kaynakların önbelleğine yeniden birleştirmenin gerekip gerekmediğini öğrenmek için kullanır `CTMENU` . Yeniden birleştirme, devenv Kurulum komutu çalıştırılarak tetiklenir.<br /><br /> Başlangıçta bu değer 1 ' e ayarlanmalıdır ve kaynaktaki her değişiklikten sonra `CTMENU` yeniden birleştirme gerçekleşmeden önce arttırılır.|  
  
### <a name="example"></a>Örnek  
 Aşağıda birkaç kaynak girişi örneği verilmiştir:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\  
  Menus\  
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10  
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackages Kullanıcı arabirimi öğeleri ekleme](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Birlikte Çalışma Bütünleştirilmiş Kodları Kullanan Komutlar ve Menüler](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)
