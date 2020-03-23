---
title: Windows'da Docker istemci hataları | Microsoft Dokümanlar
description: Visual Studio'yu kullanarak Windows'da Docker'a web uygulamaları oluşturmak ve dağıtmak için Visual Studio'yu kullanırken karşılaştığınız sorunları giderin.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027277"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>Docker ile Visual Studio geliştirme sorunlarını giderme

Visual Studio Container Tools ile çalışırken, uygulamanızı kurarken veya hata ayıklarken sorunlarla karşılaşabilirsiniz. Aşağıda bazı sık karşılaşılan sorun giderme adımları verilmiştir.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>Ses paylaşımı etkinleştirildi. Windows ayarları için Docker CE'de ses paylaşımını etkinleştirin (yalnızca Linux kapsayıcıları)

Bu sorunu çözmek için:

1. Bildirim alanında **Windows için Docker'a** sağ tıklayın ve ardından **Ayarlar'ı**seçin.
1. **Paylaşılan Sürücüler'i** seçin ve sistemin bulunduğu sürücüyle birlikte sistem sürücüsünü paylaşın.

> [!NOTE]
> Dosyalar paylaşılan görünüyorsa, "Kimlik bilgilerini sıfırla'yı" tıklatmanız gerekebilir. ses paylaşımını yeniden etkinleştirmek için iletişim kutusunun en altında bağlantı kurun. Kimlik bilgilerini sıyrıkladıktan sonra devam etmek için Visual Studio'yı yeniden başlatmanız gerekebilir.

![paylaşılan sürücüler](media/troubleshooting-docker-errors/shareddrives.png)

> [!TIP]
> Visual Studio 2017 sürümünden sonra Visual Studio **sürümleri, Paylaşılan Sürücüler** yapılandırılınca 15.6 istemi.

### <a name="container-type"></a>Konteyner tipi

Bir projeye Docker desteği eklerken, bir Windows veya Linux kapsayıcısı seçersiniz. Docker ana bilgisayar aynı kapsayıcı türünü çalıştırıyor olmalıdır. Çalışan Docker örneğinde kapsayıcı türünü değiştirmek için Sistem Tepsisi Docker simgesine sağ tıklayın ve **Windows kapsayıcılarına geçiş'i seçin...** veya **Linux kapsayıcılarına geçiş...**.

## <a name="unable-to-start-debugging"></a>Hata ayıklama başlatılamıyor

Bunun nedenlerinden biri, kullanıcı profil klasörünüzde eski hata ayıklama bileşenlerine sahip olmakla ilgili olabilir. En son hata ayıklama bileşenlerinin bir sonraki hata ayıklama oturumunda karşıdan yüklenerek bu klasörleri kaldırmak için aşağıdaki komutları uygulayın.

- del %userprofile%\vsdbg
- del %userprofile%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>Uygulamanızın hata ayıklama yaparken ağ için özel hatalar

Ev sahibi makinenizdeki ağla ilgili bileşenleri yenileyecek olan [Temizleme Kapsayıcı Ana Bilgisayar Ağı'ndan](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking)indirilebilir komut dosyasını yürütmeyi deneyin.

## <a name="mounts-denied"></a>Mounts yalanladı

macOS için Docker kullanırken, /usr/local/share/dotnet/sdk/NuGetFallbackFolder klasörüne başvuran bir hatayla karşılaşabilirsiniz. Klasörü Docker'daki Dosya Paylaşımı sekmesine ekleme

## <a name="docker-users-group"></a>Docker kullanıcıları grubu

Kapsayıcılarla çalışırken Visual Studio'da aşağıdaki hatalarla karşılaşabilirsiniz:

```
The current user must be in the 'docker-users' group to use Docker Desktop. 
Add yourself to the 'docker-users' group and then log out of Windows.
```

Docker kapsayıcılarıyla çalışma izni almak için 'docker-users' grubunun bir üyesi olmalısınız.  Windows 10'da gruba kendinizi eklemek için aşağıdaki adımları izleyin:

1. Başlat menüsünden **Bilgisayar Yönetimi'ni**açın.
1. **Yerel Kullanıcıları ve Grupları**Genişletin ve **Grupları**seçin.
1. **Docker-users** grubunu bulun, sağ tıklatın ve **gruba Ekle'yi**seçin.
1. Kullanıcı hesabınızı veya hesaplarınızı ekleyin.
1. Bu değişikliklerin etkili olması için oturum açın ve yeniden oturum açın.

Belirli gruplara `net localgroup` kullanıcı eklemek için Yönetici komut istemi'ndeki komutu da kullanabilirsiniz.

```cmd
net localgroup docker-users DOMAIN\username /add
```

PowerShell'de [Ekle-LocalGroupMember](/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember) işlevini kullanın.

## <a name="low-disk-space"></a>Düşük disk alanı

Varsayılan olarak, Docker görüntüleri genellikle sistem sürücüsünde bulunan *%ProgramData%/Docker/* klasöründe depolar, *C:\ProgramData\Docker\*. Görüntülerin sistem sürücüsünde değerli yer kaplamasını önlemek için görüntü klasörü konumunu değiştirebilirsiniz.  Görev çubuğundaki Docker simgesinden Docker ayarlarını açın, **Daemon'u**seçin ve **Basic'ten** **Advanced'e**geçin. Düzenleme bölmesinde, Docker `graph` görüntüleri için istediğiniz konumun değerini içeren özellik ayarını ekleyin:

```json
    "graph": "D:\\mypath\\images"
```

![Docker görüntü konum ayarı ekran görüntüsü](media/troubleshooting-docker-errors/docker-settings-image-location.png)

Docker'ı yeniden başlatmak için **Uygula'yı** tıklatın. Bu adımlar *% ProgramData%\docker\config\daemon.json*adresindeki yapılandırma dosyasını değiştirir. Daha önce oluşturulmuş görüntüler taşınmıyor.

## <a name="microsoftdockertools-github-repo"></a>Microsoft/DockerTools GitHub repo

Karşılaştığınız diğer sorunlar için [Microsoft/DockerTools](https://github.com/microsoft/dockertools/issues) sorunlarına bakın.