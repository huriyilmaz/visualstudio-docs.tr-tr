---
title: Windows 'da Docker istemci hatalarında sorun giderme | Microsoft Docs
description: Visual Studio kullanarak Web uygulamaları oluşturmak ve Windows üzerinde Docker 'a dağıtmak için Visual Studio kullanırken karşılaştığınız sorunları giderin.
ms.technology: vs-azure
author: ghogen
manager: jmartens
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: troubleshooting
ms.workload: multiple
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: f16ecd899bc1dddd7383ef1a815ed6197b799a19
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859534"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>Docker ile Visual Studio geliştirme sorunlarını giderme

Visual Studio kapsayıcı araçlarıyla çalışırken, uygulamanızı oluştururken veya hata ayıklarken sorunlarla karşılaşabilirsiniz. Aşağıda bazı yaygın sorun giderme adımları verilmiştir.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>Birim paylaşımı etkin değil. Docker CE for Windows ayarları 'nda birim paylaşımını etkinleştir (yalnızca Linux kapsayıcıları)

Dosya paylaşımının yalnızca Docker ile Hyper-V kullanıyorsanız yönetilmesi gerekir. WSL 2 kullanıyorsanız, aşağıdaki adımlar gerekli değildir ve dosya paylaşımı seçeneği görünür olmayacaktır. Bu sorunu çözmek için:

1. Bildirim alanında **Docker for Windows** sağ tıklatın ve ardından **Ayarlar**' ı seçin.
1. **Kaynak**  >  **Dosya Paylaşımı ' nı** seçin ve erişilmesi gereken klasörü paylaşabilirsiniz. Tüm sistem sürücünüzü paylaşma olasılığı vardır ancak önerilmez.

    ![paylaşılan sürücüler](media/troubleshooting-docker-errors/docker-settings-image.png)

> [!TIP]
> Visual Studio 2017 sürüm 15,6 ' den sonraki Visual Studio sürümleri, **paylaşılan sürücülerin** yapılandırılmadığı zaman sorar.

## <a name="unable-to-start-debugging"></a>Hata ayıklama başlatılamıyor

Bir neden, Kullanıcı profili klasörünüzde eski hata ayıklama bileşenleri bulundurmak ile ilgili olabilir. En son hata ayıklama bileşenlerinin bir sonraki hata ayıklama oturumunda indirilmesi için bu klasörleri kaldırmak üzere aşağıdaki komutları yürütün.

- del%USERPROFILE%\vsdbg
- del%userprofile%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>Uygulamanızda hata ayıklarken ağa özgü hatalar

Konuk makinenizde ağla ilgili bileşenleri yenileyecek şekilde, [Temizleme kapsayıcısı konak ağı](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking)'ndan indirilebilir betiği yürütmeyi deneyin.

## <a name="mounts-denied"></a>Bağlama reddedildi

MacOS için Docker kullanırken,/usr/local/share/DotNet/SDK/nugetfallbackfolder klasörüne başvurarak bir hatayla karşılaşabilirsiniz. Klasörü Docker 'daki dosya paylaşma sekmesine ekleyin.

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

Ayrıca, `net localgroup` kullanıcıları belirli gruplara eklemek Için yönetici komut isteminde komutunu da kullanabilirsiniz.

```cmd
net localgroup docker-users DOMAIN\username /add
```

PowerShell 'de [Add-LocalGroupMember](/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember) işlevini kullanın.

## <a name="low-disk-space"></a>Yetersiz disk alanı

Docker, varsayılan olarak, görüntüleri genellikle sistem sürücüsünde, * C:\ProgramData\Docker üzerinde bulunan *% ProgramData%/Docker/* klasöründe depolar \* . Görüntülerin sistem sürücüsünde değerli alan almasını engellemek için, görüntü klasörü konumunu değiştirebilirsiniz. Bunun için:

 1. Görev çubuğundaki Docker simgesine sağ tıklayın ve **Ayarlar**' ı seçin.
 1. **Docker altyapısını** seçin. 
 1. Düzen bölmesinde, `graph` Docker görüntüleri için istediğiniz konumun değeri ile özellik ayarını ekleyin:

```json
    "graph": "D:\\mypath\\images"
```

![Docker dosya paylaşımının ekran görüntüsü](media/troubleshooting-docker-errors/docker-daemon-settings.png)

**& yeniden başlatmak Için Uygula**' ya tıklayın. Bu adımlar *üzerinde% ProgramData% \docker\config\daemon.js* yapılandırma dosyasını değiştirir. Önceden oluşturulmuş görüntüler taşınmaz.

## <a name="container-type-mismatch"></a>Kapsayıcı türü uyumsuzluğu

Bir projeye Docker desteği eklerken bir Windows ya da Linux kapsayıcısı seçersiniz. Docker sunucu Konağı, proje hedefi ile aynı kapsayıcı türünü çalıştıracak şekilde yapılandırılmamışsa, büyük olasılıkla aşağıdakine benzer bir hata görürsünüz:

![Docker Konağı ve proje uyumsuzluğu ekran görüntüsü](media/troubleshooting-docker-errors/docker-host-config-change-linux-to-windows.png)

Bu sorunu çözmek için:

- Sistem tepsisindeki Docker for Windows simgesine sağ tıklayın ve **Windows kapsayıcılarına geç...** ' i seçin veya **Linux kapsayıcılarına geç..**..

## <a name="microsoftdockertools-github-repo"></a>Microsoft/DockerTools GitHub deposu

Karşılaştığınız diğer sorunlar için bkz.  [Microsoft/DockerTools](https://github.com/microsoft/dockertools/issues) sorunları.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio sorunlarını giderme](/troubleshoot/visualstudio/welcome-visual-studio/)
