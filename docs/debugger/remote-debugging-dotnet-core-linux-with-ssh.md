---
title: Linux 'ta uzaktan hata ayıklama .NET Core | Microsoft Docs
ms.date: 02/26/2020
ms.topic: conceptual
helpviewer_keywords:
- remote debugging, linux
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d66181f5e6720348e18c34b735ef29e24c0111a
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796309"
---
# <a name="remote-debug-net-core-on-linux-using-ssh"></a>SSH kullanarak Linux 'ta .NET Core 'da uzaktan hata ayıklama

Visual Studio 2017 ' den başlayarak, SSH üzerinden Linux üzerinde çalışan .NET Core işlemlerine iliştirebilirsiniz. Bu makalede hata ayıklamayı ayarlama ve hata ayıklama işlemlerinin nasıl yapılacağı açıklanır.

## <a name="prerequisites"></a>Ön koşullar

Visual Studio bilgisayarında, **ASP.net ve Web geliştirme** iş yükünü ya da **.NET Core platformlar arası geliştirme** iş yükünü yüklemeniz gerekir.

Linux sunucusunda SSH sunucusu yüklemeniz, unzip veya wget ile açmanız ve yüklemeniz gerekir. Örneğin, Ubuntu 'da şunu çalıştırarak şunları yapabilirsiniz:

``` cmd
sudo apt-get install openssh-server unzip curl
```

## <a name="build-and-deploy-the-application"></a>Uygulama derleme ve dağıtma

Uygulamanızı hata ayıklamaya hazırlamak için:

- Uygulamayı oluştururken bir hata ayıklama yapılandırması kullanmayı düşünün. Hata ayıklama derlenen koddan perakende koda derlenmiş kodun (sürüm yapılandırması) hata ayıklaması çok daha zordur. Sürüm yapılandırması kullanmanız gerekiyorsa Yalnızca kendi kodum önce devre dışı bırakın. Bu ayarı devre dışı bırakmak için **Araçlar**  >  **Seçenekler**  >  **hata ayıklama** ' ı seçin ve ardından **yalnızca kendi kodum etkinleştir** ' i kaldırın.

- Projenizin [Taşınabilir pdb 'leri](https://github.com/OmniSharp/omnisharp-vscode/wiki/Portable-PDBs) (varsayılan ayar) olarak yapılandırıldığından emin olun ve PBX 'lerin dll ile aynı konumda olduğundan emin olun. Visual Studio 'da yapılandırmak için projeye sağ tıklayın ve ardından **Özellikler**  >  **Build**  >  **Gelişmiş**  >  **hata ayıklama bilgileri** oluştur ' u seçin.

Hata ayıklamadan önce uygulamayı dağıtmak için çeşitli yöntemler kullanabilirsiniz. Örneğin, şunları yapabilirsiniz:

- Kaynakları hedef bilgisayara kopyalayın ve Linux makinesinde ile derleyin ```dotnet build``` .

- Uygulamayı Windows üzerinde oluşturun ve ardından derleme yapıtlarını Linux makinesine aktarın. (Yapı yapıtları uygulamanın kendisinden, bağlı olabileceği çalışma zamanı kitaplıklarının ve dosyadaki *.deps.js* .)

## <a name="attach-the-debugger"></a>Hata ayıklayıcıyı iliştirme

Bilgisayarlar yapılandırıldıktan sonra, uygulamayı Linux makinesinde başlatın ve ardından hata ayıklayıcıyı eklemeye hazırlanın.

1. Visual Studio 'da **Hata Ayıkla**  >  **işleme Ekle...** seçeneğini belirleyin.

1. **Bağlantı türü** listesinde **SSH** ' ı seçin.

1. **Bağlantı hedefini** hedef bilgisayarın IP adresi veya ana bilgisayar adıyla değiştirin.

1. Hata ayıklamak istediğiniz işlemi bulun.

   Kodunuz, benzersiz bir işlem adında veya DotNet adlı bir işlemde çalışır. İlgilendiğiniz işlemi bulmak için, işlem için komut satırı bağımsız değişkenlerini gösteren **başlık** sütununu kontrol edin.

   Aşağıdaki örnekte, **Işleme İliştir** iletişim kutusunda bir SSH taşıması üzerinden uzak bir Linux makinesinden işlemlerin listesini görürsünüz.

   ![Linux işlemine iliştir](media/remote-debug-linux-over-ssh-attach.png)

1. **Ekle** ' yi seçin.

1. Görüntülenen iletişim kutusunda, hata ayıklamak istediğiniz kod türünü seçin. **Yönetilen (UNIX için .NET Core)** seçeneğini belirleyin.

1. Uygulamada hata ayıklamak için Visual Studio hata ayıklama özelliklerini kullanın.

   Aşağıdaki örnekte, Visual Studio hata ayıklayıcının uzak bir Linux makinesinde çalışan koddaki bir kesme noktasında durdurulduğunu görürsünüz.

   ![Kesme noktasına isabet edin](media/remote-debug-linux-over-ssh-hit-breakpoint.png)