---
title: Windows Docker istemcisi hatalarında sorun giderme | Microsoft Docs
description: Visual Studio kullanarak Web uygulamaları oluşturmak ve Windows üzerinde Docker 'a dağıtmak için Visual Studio kullanırken karşılaştığınız sorunları giderin.
ms.technology: vs-azure
author: ghogen
manager: jillfra
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: conceptual
ms.workload: multiple
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: d8aa3028a12bcfb49f2663b2bea688baf14fd7f2
ms.sourcegitcommit: b2fc9ac7d73c847508f6ed082bed026476bb3955
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/05/2020
ms.locfileid: "77027277"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>Docker ile Visual Studio geliştirme sorunlarını giderme

Visual Studio kapsayıcı araçlarıyla çalışırken, uygulamanızı oluştururken veya hata ayıklarken sorunlarla karşılaşabilirsiniz. Aşağıda bazı ortak adımlar giderirken.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>Birim paylaşımı etkin değil. Birim, paylaşım için Docker CE Windows ayarları (yalnızca Linux kapsayıcıları) etkinleştir

Bu sorunu çözmek için:

1. Bildirim alanında **Docker for Windows** sağ tıklatın ve ardından **Ayarlar**' ı seçin.
1. **Paylaşılan sürücüler** ' i seçin ve sistem sürücüsünü projenin bulunduğu sürücüyle birlikte paylaşabilirsiniz.

> [!NOTE]
> Dosyaları paylaşılan görünüyorsa, birimi paylaşan yeniden etkinleştirmek için iletişim kutusunun alt kısmındaki "... kimlik bilgilerini Sıfırla" bağlantısını tıklatın gerekebilir. Kimlik bilgilerini sıfırlama sonra devam etmek için Visual Studio'yu yeniden başlatmanız gerekebilir.

![Paylaşılan sürücüleri](media/troubleshooting-docker-errors/shareddrives.png)

> [!TIP]
> **Paylaşılan sürücüler** yapılandırılmadığında visual Studio 2017 sürüm 15,6 ' den sonraki Visual Studio sürümleri istemi.

### <a name="container-type"></a>Kapsayıcı türü

Bir projeye Docker desteği eklerken bir Windows ya da Linux kapsayıcısı seçersiniz. Docker ana bilgisayarı aynı kapsayıcı türünü çalıştırıyor olmalıdır. Çalışan Docker örneğindeki kapsayıcı türünü değiştirmek için, sistem tepsisinin Docker simgesine sağ tıklayın ve **Windows kapsayıcılarına geç...** ' i seçin veya **Linux kapsayıcılarına geç..** ..

## <a name="unable-to-start-debugging"></a>Hata ayıklama başlatılamıyor

Nedenlerinden biri, kullanıcı profili klasöründe eski hata ayıklama bileşenleri bulunması ilgili olabilir. En son hata ayıklama bileşenleri sonraki hata ayıklama oturumunda yüklenir, böylece bu klasörleri kaldırmak için aşağıdaki komutları yürütün.

- DEL %userprofile%\vsdbg
- DEL %userprofile%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>Uygulamanızı hata ayıklama sırasında ağ ile belirli hataları

Konuk makinenizde ağla ilgili bileşenleri yenileyecek şekilde, [Temizleme kapsayıcısı konak ağı](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking)'ndan indirilebilir betiği yürütmeyi deneyin.

## <a name="mounts-denied"></a>Takar reddedildi

MacOS için Docker'ı kullanırken, klasör /usr/local/share/dotnet/sdk/NuGetFallbackFolder başvuran bir hatayla karşılaşabilir. Docker dosya paylaşımı sekmesine klasörü Ekle

## <a name="docker-users-group"></a>Docker kullanıcıları grubu

Kapsayıcılarla çalışırken Visual Studio 'da aşağıdaki hatayla karşılaşabilirsiniz:

```
The current user must be in the 'docker-users' group to use Docker Desktop. 
Add yourself to the 'docker-users' group and then log out of Windows.
```

Docker kapsayıcılarıyla çalışma izinlerinin olması için ' Docker-Users ' grubunun bir üyesi olmanız gerekir.  Windows 10 ' da gruba eklemek için aşağıdaki adımları izleyin:

1. Başlat menüsünden **Bilgisayar Yönetimi**' ni açın.
1. **Yerel kullanıcılar ve gruplar**' ı genişletin ve **gruplar**' ı seçin.
1. **Docker-Users** grubunu bulun, sağ tıklayın ve **gruba ekle**' yi seçin.
1. Kullanıcı hesabınızı veya hesaplarınızı ekleyin.
1. Bu değişikliklerin etkili olması için oturumu kapatın ve yeniden oturum açın.

Ayrıca, kullanıcıları belirli gruplara eklemek için yönetici komut isteminde `net localgroup` komutunu da kullanabilirsiniz.

```cmd
net localgroup docker-users DOMAIN\username /add
```

PowerShell 'de [Add-LocalGroupMember](/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember) işlevini kullanın.

## <a name="low-disk-space"></a>Yetersiz disk alanı

Docker, varsayılan olarak, görüntüleri genellikle sistem sürücüsünde, * C:\ProgramData\Docker\* *% ProgramData%/Docker/* klasöründe depolar. Görüntülerin sistem sürücüsünde değerli alan almasını engellemek için, görüntü klasörü konumunu değiştirebilirsiniz.  Görev çubuğundaki Docker simgesinden Docker ayarlarını açın, **Daemon**' ı seçin ve **temel** ' ten **Gelişmiş**' e geçin. Düzen bölmesinde, Docker görüntüleri için istediğiniz konumun değeri ile `graph` özellik ayarını ekleyin:

```json
    "graph": "D:\\mypath\\images"
```

![Docker görüntüsü konum ayarının ekran görüntüsü](media/troubleshooting-docker-errors/docker-settings-image-location.png)

Docker 'ı yeniden başlatmak için **Uygula** ' ya tıklayın. Bu adımlar *%ProgramData%\docker\config\daemon.JSON*adresindeki yapılandırma dosyasını değiştirir. Önceden oluşturulmuş görüntüler taşınmaz.

## <a name="microsoftdockertools-github-repo"></a>Microsoft/DockerTools GitHub deposu

Karşılaştığınız diğer sorunlar için bkz. [Microsoft/DockerTools](https://github.com/microsoft/dockertools/issues) sorunları.