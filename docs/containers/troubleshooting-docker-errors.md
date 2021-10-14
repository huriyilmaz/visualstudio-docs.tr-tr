---
title: Windows Docker istemci hatalarında sorun giderme | Microsoft Docs
description: Visual Studio kullanarak Windows docker 'a web uygulamaları oluşturmak ve dağıtmak için Visual Studio kullanırken karşılaştığınız sorunları giderin.
ms.technology: vs-container-tools
author: ghogen
manager: jmartens
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: troubleshooting
ms.workload: multiple
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: 5bead44960453af7410d89cea4b5eca05945a6fb
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129970223"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>Docker ile Visual Studio geliştirme sorunlarını giderme

Visual Studio kapsayıcı araçlarıyla çalışırken, uygulamanızı derlerken veya hata ayıklarken sorunlarla karşılaşabilirsiniz. Aşağıda bazı yaygın sorun giderme adımları verilmiştir.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>Birim paylaşımı etkin değil. Docker CE for Windows ayarları 'nda birim paylaşımını etkinleştir (yalnızca Linux kapsayıcıları)

Dosya paylaşımının yalnızca Docker ile Hyper-V kullanıyorsanız yönetilmesi gerekir. WSL 2 kullanıyorsanız, aşağıdaki adımlar gerekli değildir ve dosya paylaşımı seçeneği görünür olmayacaktır. Bu sorunu çözmek için:

1. bildirim alanında **Docker for Windows** sağ tıklayın ve **Ayarlar**' ı seçin.
1. **Kaynak**  >  **Dosya Paylaşımı ' nı** seçin ve erişilmesi gereken klasörü paylaşabilirsiniz. Tüm sistem sürücünüzü paylaşma olasılığı vardır ancak önerilmez.

    :::image type="content" source="media//troubleshooting-docker-errors/docker-settings-image.png" alt-text="Paylaşılan sürücüler":::

> [!TIP]
> Visual Studio 2017 sürüm 15,6 ' den sonraki Visual Studio sürümler, **paylaşılan sürücülerin** yapılandırılmadığı zaman sorar.

## <a name="unable-to-start-debugging"></a>Hata ayıklama başlatılamıyor

Bir neden, Kullanıcı profili klasörünüzde eski hata ayıklama bileşenleri bulundurmak ile ilgili olabilir. En son hata ayıklama bileşenlerinin bir sonraki hata ayıklama oturumunda indirilmesi için bu klasörleri kaldırmak üzere aşağıdaki komutları yürütün.

- del%USERPROFILE%\vsdbg
- del%userprofile%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>Uygulamanızda hata ayıklarken ağa özgü hatalar

Konuk makinenizde ağla ilgili bileşenleri yenileyecek şekilde, [Temizleme kapsayıcısı konak ağı](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking)'ndan indirilebilir betiği yürütmeyi deneyin.

## <a name="mounts-denied"></a>Bağlama reddedildi

MacOS için Docker kullanırken,/usr/local/share/DotNet/SDK/nugetfallbackfolder klasörüne başvurarak bir hatayla karşılaşabilirsiniz. Klasörü Docker 'daki dosya paylaşma sekmesine ekleyin.

## <a name="docker-users-group"></a>Docker kullanıcıları grubu

kapsayıcılarla çalışırken Visual Studio aşağıdaki hatayla karşılaşabilirsiniz:

```
The current user must be in the 'docker-users' group to use Docker Desktop. 
Add yourself to the 'docker-users' group and then log out of Windows.
```

Docker kapsayıcılarıyla çalışma izinlerinin olması için ' Docker-Users ' grubunun bir üyesi olmanız gerekir.  kendinizi Windows 10 gruba eklemek için aşağıdaki adımları izleyin:

1. Başlat menüsü, **bilgisayar yönetimi**' ni açın.
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

 1. görev çubuğunda docker simgesine sağ tıklayın ve **Ayarlar**' yi seçin.
 1. **Docker altyapısını** seçin. 
 1. Düzen bölmesinde, `graph` Docker görüntüleri için istediğiniz konumun değeri ile özellik ayarını ekleyin:

```json
    "graph": "D:\\mypath\\images"
```

:::image type="content" source="media/troubleshooting-docker-errors/docker-daemon-settings.png" alt-text="Docker dosya paylaşımının ekran görüntüsü":::

**& yeniden başlatmak Için Uygula**' ya tıklayın. Bu adımlar *%ProgramData%\docker\config\daemon.JSON* adresindeki yapılandırma dosyasını değiştirir. Önceden oluşturulmuş görüntüler taşınmaz.

## <a name="container-type-mismatch"></a>Kapsayıcı türü uyumsuzluğu

bir projeye docker desteği eklerken bir Windows veya Linux kapsayıcısı seçersiniz. Docker sunucu Konağı, proje hedefi ile aynı kapsayıcı türünü çalıştıracak şekilde yapılandırılmamışsa, büyük olasılıkla aşağıdakine benzer bir hata görürsünüz:

:::image type="content" source="media/troubleshooting-docker-errors/docker-host-config-change-linux-to-windows.png" alt-text="docker konağı ve Project uyumsuzluğu ekran görüntüsü":::

Bu sorunu çözmek için:

- sistem tepsisindeki Docker for Windows simgesine sağ tıklayın ve **Windows kapsayıcılar...** ' a geçin veya **Linux kapsayıcılarına geç..**. ' i seçin.

## <a name="microsoftdockertools-github-repo"></a>Microsoft/dockertools GitHub deposu

Karşılaştığınız diğer sorunlar için bkz.  [Microsoft/DockerTools](https://github.com/microsoft/dockertools/issues) sorunları.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio sorunlarını giderme](/troubleshoot/visualstudio/welcome-visual-studio/)
