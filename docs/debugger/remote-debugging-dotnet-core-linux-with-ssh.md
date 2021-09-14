---
title: Linux’ta .NET Core hatalarını ayıklama
description: Bir işleme ek olarak Linux üzerinde .NET Core Secure Shell (SSH) kullanarak hata ayıklar. Uygulamalarınızı hata ayıklama için hazırlayın. Uygulamayı derleme ve dağıtma. Hata ayıklayıcıyı iliştirin.
ms.custom: SEO-VS-2020
ms.date: 08/24/2021
ms.topic: conceptual
helpviewer_keywords:
- remote debugging, linux
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 71f9c74e37eafcd8bdaa9e0f9da361a6684c7d4b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627909"
---
# <a name="debug-net-core-on-linux-using-ssh-by-attaching-to-a-process"></a>Bir işleme ek olarak SSH kullanarak Linux'ta .NET Core'da hata ayıklama

2017'Visual Studio başlayarak, SSH üzerinden yerel veya uzak bir Linux dağıtımında çalışan .NET Core işlemlerine iliştirebilirsiniz. Bu makalede hata ayıklamayı ayarlama ve hata ayıklama açıklanmıştır. Docker kapsayıcılarını kullanan senaryolarda hata ayıklama için [bkz. Docker](../debugger/attach-to-process-running-in-docker-container.md) kapsayıcısı üzerinde çalışan bir işleme ekleme ve bunun [yerine kapsayıcı araçları](../containers/edit-and-refresh.md) makaleleri. WSL 2'de Linux'ta hata ayıklamak Visual Studio (işlemeye eklemeden), bkz. [WSL 2'de .NET Core Apps'te](../debugger/debug-dotnet-core-in-wsl-2.md)Visual Studio.

## <a name="prerequisites"></a>Önkoşullar

- Bu Visual Studio, ASP.NET **ve web** geliştirme iş yükünü veya **.NET Core** platformlar arası geliştirme iş yükünü yüklemeniz gerekir.

- Linux sunucusunda SSH sunucusunu yüklemeniz, curl veya wget ile sıkıştırmayı açıp yüklemeniz gerekir. Örneğin Ubuntu'da şunları çalıştırarak bunu yapabiliriz:

  ``` cmd
  sudo apt-get install openssh-server unzip curl
  ```

  SFTP'nin yanı sıra SSH de etkinleştirilmelidir. Çoğu SSH dağıtımı varsayılan olarak SFTP'yi yükp etkinleştirir, ancak her zaman böyle değildir.

- Linux sunucusunda, [.NET çalışma zamanını Linux'a](/dotnet/core/install/linux)yükleyin ve Linux dağıtımınıza (Ubuntu gibi) uyan sayfayı bulun. .NET SDK gerekli değildir.

- Kapsamlı ASP.NET Core için bkz. [Nginx ile Linux üzerinde](/aspnet/core/host-and-deploy/linux-nginx) konak ASP.NET Core ve Apache ile [Linux'ta Konak ASP.NET Core.](/aspnet/core/host-and-deploy/linux-apache)

## <a name="prepare-your-application-for-debugging"></a>Uygulamalarınızı hata ayıklama için hazırlama

Uygulamalarınızı hata ayıklamaya hazırlamak için:

- Uygulamayı derlemek için Hata Ayıklama yapılandırması kullanmayı göz önünde bulundurabilirsiniz. Perakende olarak derlenmiş kodun (Yayın yapılandırması) hata ayıklaması, hata ayıklama kodundan çok daha zordur. Yayın yapılandırmasına ihtiyacınız varsa önce yapılandırmayı devre dışı Yalnızca kendi kodum. Bu ayarı devre dışı bırakmak için Araçlar **Seçenekler**  >  **Hata**  >  **Ayıklama'ya tıklayın** ve ardından Etkinleştir'in seçimini **Yalnızca kendi kodum.**

- Projenizin taşınabilir PDB'ler [üretecek](https://github.com/OmniSharp/omnisharp-vscode/wiki/Portable-PDBs) şekilde yapılandırıldığından emin olun (varsayılan ayardır) ve PDB'lerin DLL ile aynı konumda olduğundan emin olun. Bu yapılandırmayı Visual Studio için projeye sağ tıklayın, ardından Özellikler Gelişmiş Hata **Ayıklama** Bilgileri  >    >  **Derleme'yi**  >  **seçin.**

## <a name="build-and-deploy-the-application"></a>Uygulama derleme ve dağıtma

Hata ayıklamadan önce uygulamayı dağıtmak için çeşitli yöntemler kullanabilirsiniz. Örneğin, şunları yapabilirsiniz:

- Kaynakları hedef bilgisayara kopyalayın ve Linux makinesi ```dotnet build``` üzerinde ile derlemeyi başlatın.

- Uygulamayı Windows ve ardından derleme yapıtlarını Linux makinesine aktarabilirsiniz. (Derleme yapıtları uygulamanın kendisini, taşınabilir PDB'leri, bağımlı olabileceği tüm çalışma zamanı kitaplıklarını ve *.deps.json dosyasından* oluşur.)

Uygulama dağıtıldığında uygulamayı başlatabilirsiniz.

## <a name="attach-the-debugger"></a>Hata ayıklayıcıyı ekleme

Uygulama Linux makinede çalıştırıldıkları zaman hata ayıklayıcıyı eklemeye hazır olur.

1. Bu Visual Studio, İşleme **Ekle... hata**  >  **ayıkla'ya seçin.**

1. Bağlantı **Türü listesinde** **SSH'yi seçin.**

1. Bağlantı **Hedefi'ne** hedef bilgisayarın IP adresini veya ana bilgisayar adını yazın.

   Daha önce kimlik bilgilerini girmedıysanız parola ve/veya özel anahtar dosyası girmeniz istenir.

   SSH sunucusunun üzerinde çalıştırılan bağlantı noktası dışında yapılandırılması gereken bağlantı noktası gereksinimleri yoktur.

1. Hata ayıklamak için gereken işlemi bulun.

   Kodunuz benzersiz bir işlem adında veya dotnet adlı bir işlemde çalışır. İlgilenilen işlemi bulmak için, işlem için **komut** satırı bağımsız değişkenlerini gösteren Başlık sütununu kontrol edin.

   Aşağıdaki örnekte, İşleme Ekle iletişim kutusunda bir SSH taşıması üzerinden uzak Bir Linux makineden **gelen işlemlerin listesini** görüyorsunuz.

   ![Linux sürecine ekleme](media/remote-debug-linux-over-ssh-attach.png)

1. **Ekle'yi seçin.**

1. Görüntülenen iletişim kutusunda, hata ayıklamak istediğiniz kod türünü seçin. Yönetilen **(Unix için .NET Core) 'ı seçin.**

1. Uygulamada Visual Studio ayıklamak için hata ayıklama özelliklerini kullanın.

   Aşağıdaki örnekte, uzak Bir Linux Visual Studio çalışan kodda kesme noktası sırasında durdurulan hata ayıklayıcısını görüyorsunuz.

   ![Kesme noktası isabeti](media/remote-debug-linux-over-ssh-hit-breakpoint.png)