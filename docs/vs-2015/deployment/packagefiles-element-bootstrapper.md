---
title: '&lt;PackageFiles &gt; öğesi (önyükleyici) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <PackageFiles> element [bootstrapper]
ms.assetid: 3ea252d7-18a3-47d8-af83-47feebcfe82b
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 382689dada13adce1ee530e66fef6ba78452efaa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188978"
---
# <a name="ltpackagefilesgt-element-bootstrapper"></a>&lt;PackageFiles &gt; öğesi (önyükleyici)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`PackageFiles`Öğesi, `PackageFile` öğesinin sonucu olarak yürütülen yükleme paketlerini tanımlayan öğeleri içerir `Command` .  
  
## <a name="syntax"></a>Syntax  
  
```  
<PackageFiles  
    CopyAllPackageFiles  
>  
    <PackageFile   
        Name  
        HomeSite  
        CopyOnBuild  
        PublicKey  
        Hash  
    />  
</PackageFiles>  
```  
  
## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler  
 `PackageFiles`Öğesi aşağıdaki özniteliğe sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`CopyAllPackageFiles`|İsteğe bağlı. Olarak ayarlanırsa `false` , yükleyici yalnızca öğeden başvurulan dosyaları indirir `Command` . Olarak ayarlanırsa `true` , tüm dosyalar indirilir.<br /><br /> Olarak ayarlanırsa `IfNotHomesite` , yükleyici, olarak ayarlanmış gibi davranır `False` `ComponentsLocation` `HomeSite` ve aksi takdirde aynı `True` şekilde çalışır. Bu ayar, kendisine ait önyükleme yapan paketlerin bir HomeSite senaryosunda kendi davranışlarını yürütmesine olanak tanımak için yararlı olabilir.<br /><br /> Varsayılan değer: `true`.|  
  
## <a name="packagefile"></a>PackageFile  
 `PackageFile`Öğesi, öğesinin bir alt öğesidir `PackageFiles` . Bir `PackageFiles` öğe en az bir öğe içermelidir `PackageFile` .  
  
 `PackageFile` Aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Name`|Gereklidir. Paket dosyasının adı. Bu, `Command` bir paketin yüklendiği koşulları tanımladığında öğenin başvurulacağını olan addır. Bu değer Ayrıca, `Strings` [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] paketin, paketi tanımlamakta kullanacağı yerelleştirilmiş adı almak için tabloya bir anahtar olarak da kullanılır.|  
|`HomeSite`|İsteğe bağlı. Yükleyiciye dahil değilse, uzak sunucudaki paketin konumu.|  
|`CopyOnBuild`|İsteğe bağlı. Önyükleyici 'nin, derleme zamanında paket dosyasını diske kopyalaması gerekip gerekmediğini belirtir. Varsayılan değer true 'dur.|  
|`PublicKey`|Paketin sertifika imzalayan şifreli ortak anahtar. Kullanılıyorsa gereklidir `HomeSite` ; Aksi takdirde, isteğe bağlıdır.|  
|`Hash`|İsteğe bağlı. Paket dosyasının SHA1 karması. Bu, yüklemenin zamanında dosyanın bütünlüğünü doğrulamak için kullanılır. Aynı karma paket dosyasından hesaplanamaz, paket yüklenmez.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] yeniden dağıtılabilir paket için paketleri ve Windows Installer gibi bağımlılıklarını tanımlar.  
  
```  
<PackageFiles>  
    <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>  
    <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetchk.exe"/>  
</PackageFiles>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<Product> Dosyalarında](../deployment/product-element-bootstrapper.md)   
 [\<Package> Dosyalarında](../deployment/package-element-bootstrapper.md)   
 [Ürün ve Paket Şema Başvurusu](../deployment/product-and-package-schema-reference.md)
