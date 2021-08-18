---
title: Linux’ta .NET Core hatalarını ayıklama
description: Bir işleme ekleyerek Linux üzerinde .NET Core 'a hata ayıklayın Secure Shell (SSH) kullanarak. Uygulamanızı hata ayıklama için hazırlayın. Uygulamayı derleyin ve dağıtın. Hata ayıklayıcıyı iliştirin.
ms.custom: SEO-VS-2020
ms.date: 02/26/2020
ms.topic: conceptual
helpviewer_keywords:
- remote debugging, linux
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: de1827e2cf6aa7065c730cabcee0c9d61f1f4c12
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065247"
---
# <a name="debug-net-core-on-linux-using-ssh-by-attaching-to-a-process"></a>Bir işleme ekleyerek SSH kullanarak Linux 'ta .NET Core hatalarını ayıklama

Visual Studio 2017 ' den başlayarak, SSH üzerinden yerel veya uzak bir Linux dağıtımında çalışan .net Core işlemlerine iliştirebilirsiniz. Bu makalede hata ayıklamayı ayarlama ve hata ayıklama işlemlerinin nasıl yapılacağı açıklanır. Docker kapsayıcılarını kullanan senaryoları hata ayıklama için bkz. [bir Docker kapsayıcısında çalışan bir işleme](../debugger/attach-to-process-running-in-docker-container.md) ve bunun yerine [kapsayıcı araçları](../containers/edit-and-refresh.md) makalelerine iliştirme. Visual Studio 'den wsl 2 ' de Linux 'ta hata ayıklamak için (işleme iliştirme), bkz. [Visual Studio ile wsl 2 içindeki .net Core uygulamalarında hata ayıklama](../debugger/debug-dotnet-core-in-wsl-2.md).

## <a name="prerequisites"></a>Önkoşullar

- Visual Studio bilgisayarda, **ASP.NET ve web geliştirme** iş yükünü ya da **.net Core platformlar arası geliştirme** iş yükünü yüklemeniz gerekir.

- Linux sunucusunda SSH sunucusu yüklemeniz, unzip veya wget ile açmanız ve yüklemeniz gerekir. Örneğin, Ubuntu 'da şunu çalıştırarak şunları yapabilirsiniz:

  ``` cmd
  sudo apt-get install openssh-server unzip curl
  ```

- Linux sunucusunda, Linux ['a .NET çalışma zamanını yükledikten](/dotnet/core/install/linux)sonra Linux dağıtımınızı (Ubuntu gibi) eşleştiren sayfayı bulun. .NET SDK gerekli değildir.

- kapsamlı ASP.NET Core yönergeler için bkz. [linux üzerinde host ASP.NET Core For ngınx](/aspnet/core/host-and-deploy/linux-nginx) ve [host ASP.NET Core Apache ile linux üzerinde](/aspnet/core/host-and-deploy/linux-apache).

## <a name="prepare-your-application-for-debugging"></a>Uygulamanızı hata ayıklama için hazırlama

Uygulamanızı hata ayıklamaya hazırlamak için:

- Uygulamayı oluştururken bir hata ayıklama yapılandırması kullanmayı düşünün. Hata ayıklama derlenen koddan perakende koda derlenmiş kodun (sürüm yapılandırması) hata ayıklaması çok daha zordur. Sürüm yapılandırması kullanmanız gerekiyorsa Yalnızca kendi kodum önce devre dışı bırakın. Bu ayarı devre dışı bırakmak için **Araçlar**  >  **Seçenekler**  >  **hata ayıklama**' ı seçin ve ardından **yalnızca kendi kodum etkinleştir**' i kaldırın.

- Projenizin [Taşınabilir pdb 'leri](https://github.com/OmniSharp/omnisharp-vscode/wiki/Portable-PDBs) (varsayılan ayar) olarak yapılandırıldığından ve PDB 'LERI 'in dll ile aynı konumda olduğundan emin olun. bunu Visual Studio yapılandırmak için projeye sağ tıklayın ve ardından **özellikler**  >    >  **gelişmiş**  >  **hata ayıklama bilgileri** oluştur ' u seçin.

## <a name="build-and-deploy-the-application"></a>Uygulama derleme ve dağıtma

Hata ayıklamadan önce uygulamayı dağıtmak için çeşitli yöntemler kullanabilirsiniz. Örneğin, şunları yapabilirsiniz:

- Kaynakları hedef bilgisayara kopyalayın ve Linux makinesinde ile derleyin ```dotnet build``` .

- Windows uygulamayı oluşturun ve ardından derleme yapıtlarını Linux makinesine aktarın. (Yapı yapıtları uygulamanın kendisini, taşınabilir pdb 'leri, bağlı olabileceği tüm çalışma zamanı kitaplıklarını ve dosyadaki *.deps.js* oluşur.)

Uygulama dağıtıldığında uygulamayı başlatın.

## <a name="attach-the-debugger"></a>Hata ayıklayıcıyı iliştirme

Uygulama Linux makinesinde çalışırken, hata ayıklayıcıyı eklemeye hazırız.

1. Visual Studio, işleme ekle **hata ayıkla**  >  **...** seçeneğini belirleyin.

1. **Bağlantı türü** listesinde **SSH**' ı seçin.

1. **Bağlantı hedefini** hedef bilgisayarın IP adresi veya ana bilgisayar adıyla değiştirin.

   Kimlik bilgilerini henüz sağlamadıysanız, bir parola ve/veya özel anahtar dosyası girmeniz istenir.

   SSH sunucusunun üzerinde çalıştığı bağlantı noktası dışında, yapılandırılacak bir bağlantı noktası gereksinimi yoktur.

1. Hata ayıklamak istediğiniz işlemi bulun.

   Kodunuz, benzersiz bir işlem adında veya DotNet adlı bir işlemde çalışır. İlgilendiğiniz işlemi bulmak için, işlem için komut satırı bağımsız değişkenlerini gösteren **başlık** sütununu kontrol edin.

   Aşağıdaki örnekte, **Işleme İliştir** iletişim kutusunda bir SSH taşıması üzerinden uzak bir Linux makinesinden işlemlerin listesini görürsünüz.

   ![Linux işlemine iliştir](media/remote-debug-linux-over-ssh-attach.png)

1. **Ekle**' yi seçin.

1. Görüntülenen iletişim kutusunda, hata ayıklamak istediğiniz kod türünü seçin. **Yönetilen (UNIX için .NET Core)** seçeneğini belirleyin.

1. uygulamada hata ayıklamak için Visual Studio hata ayıklama özelliklerini kullanın.

   aşağıdaki örnekte, uzak bir Linux makinesinde çalışan koddaki bir kesme noktasında Visual Studio hata ayıklayıcının durdurulduğunu görürsünüz.

   ![Kesme noktasına isabet edin](media/remote-debug-linux-over-ssh-hit-breakpoint.png)