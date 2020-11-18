---
title: Codespace 'i özelleştirme (Önizleme)
description: Codespace 'i özelleştirme hakkında daha fazla bilgi edinin.
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: 9072676dfc96ffc6286f81785048eca8ec46b0b8
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850513"
---
# <a name="how-to-customize-a-codespace-preview"></a>Codespace 'i özelleştirme (Önizleme)

GitHub Codespaces, bulutta tam bir geliştirme ortamı sağlar. Visual Studio 2019 kullanarak Windows tabanlı geliştirmede, GitHub Codespaces varsayılan örnekleri harika bir başlangıç noktası sağlar ancak Ayrıca, belirli projeniz için ortamı özelleştirebilirsiniz.

## <a name="installed-software"></a>Yüklü yazılım

Hemen kullanmaya başlamak için Windows codespaces, zaten yüklü birçok çerçeve ve araç ile gelir. Aşağıdaki tabloda, tüm Windows codespace ortamlarında bulunan uygulamalar ve özellikler listelenmiştir.

| Uygulama                                         | Yol diğer adı | Sürüm            |
|---------------------------------------------|------------|--------------------|
| .NET                                        | YOK        | 4.8                |
| .NET Core Runtime                           | dotnet     | 2,1, 3,1           |
| .NET Core SDK                               | dotnet     | 2,1, 3.1.3, 3.1.4  |
| Azure CLI’si                                   | az         | 2.5                |
| Chocolatey                                  | Choco      | 0.10.15            |
| CMake                                       | CMake      | 3,17               |
| Git                                         | git        | 2,26               |
| Microsoft derleme                             | MSBUILD    | 16,7               |
| Microsoft SQL Server Express Edition 2019   | YOK        | 15.0               |
| Ninja                                       | Ninja      | 1.8.2              |
| Node.js                                     | node       | 12,16              |
| NPM                                         | npm        | 6,14               |
| Python                                      | python     | 3.7                |
| VC Paket Yöneticisi                          | vcpkg      | 2020,02            |
| Windows SDK’sı                                 | YOK        | 10.0.18362         |

Yukarıdaki liste ayrıntılı değildir ve Visual Studio 'Nun yüklediği birçok aracı dışlar (örneğin, IISExpress). Bir bileşen, yukarıda belirtilenden farklı bir küçük veya yayama sürümüne de sahip olabilir.

Önceden yüklenmiş çerçeveler ve araçlar hakkında belirli Ayrıntılar aşağıdaki [yüklü yazılım özellikleri](#installed-software-specifics) bölümünde verilmiştir.

## <a name="modifications-to-a-codespace"></a>Codespace üzerinde yapılan değişiklikler
 
Bir codespace oluşturduktan sonra, codespace örneği GitHub Codespaces 'da kullanılabilir olduğunda, söz konusu codespace üzerinde yapılan tüm değişiklikler kalıcı hale getirilir. Ek depoları kopyalayabilir, Araçlar ve uygulama üreticileri yükleyebilir ve başka geliştirme varlıkları ekleyebilirsiniz ve bu değişiklikler, codespace askıya alındığında bile korunacaktır. Ancak bir codespace silerseniz, tüm değişiklikler silinir.

> [!NOTE]
> Bir codespace silerseniz, codespace 'teki bir yerel depoda (bekleyen veya kaydedilmiş) değişiklikler kaybedilir. Bir codespace silinmeden önce depo değişikliklerini uzak bir konuma gönderdiğinizden emin olun.

Visual Studio ile bir codespace 'e bağlıyken, komut satırı araçlarını çalıştırmak için Visual Studio terminalini kullanabilirsiniz. PowerShell veya Windows komut Istemi ' ni, her ikisi de yerel yönetici hesabı altında yükseltilmiş olarak kullanabilirsiniz. Visual Studio terminali hakkında daha fazla bilgi edinmek için bkz. [Visual Studio Terminal duyurusu blogu](https://devblogs.microsoft.com/visualstudio/say-hello-to-the-new-visual-studio-terminal/).

## <a name="customize-a-codespace"></a>Codespace’i özelleştirme

GitHub Codespaces 'ın gerçek değeri, bulutta kendi çalışmanız ve ekibiniz için özel olarak tasarlanmış benzersiz ve yinelenebilir geliştirme ortamları oluşturabileceğiniz zaman gelir. Varsayılan bir GitHub Codespaces örneği oluşturarak, yeni bir kod alanı oluştururken nelerin yüklendiğini ve yapılandırıldığını özelleştirebilirsiniz.

Sonraki bölümlerde *.devcontainer.json* ve *.devinit.js* dosyaları kullanılarak iki codespace yapılandırma yöntemi anlatılacaktır. Bu dosyalar, bir codespace için yükleme çerçevelerini ve araçları yapılandırmanıza ve deponuza eklendiğinde, deponuza göre codespace oluşturan herkes aynı uzak geliştirme ortamına sahip olacaktır.

## <a name="customize-with-devcontainerjson"></a>devcontainer.jsile Özelleştir

Bir codespace oluşturulduğunda, GitHub Codespaces, deponuzın kökündeki bir [*devcontainers.js*](https://code.visualstudio.com/docs/remote/devcontainerjson-reference) arar ve codespace 'i veya buna bağlanan istemci örneklerini özelleştirmek için içindeki ayarları kullanır (tarayıcı-temel düzenleyici, Visual Studio veya Visual Studio Code). Çoğu ayar *devcontainer.js* , Linux tabanlı kod alanları veya diğer iki istemci için geçerlidir ancak bazıları Windows codespaces ve Visual Studio 'da kullanılabilir.

Dosyadaki *devcontainer.js* , bir depodaki iki konumdan birine yerleştirilebilir:

1. *{Repository-root}/.devcontainer.json*
2. *{Repository-root}/.exe devcontainer/devcontainer.json*

GitHub Codespaces, özelliklerde aşağıdaki *devcontainer.js* destekler. Visual Studio 'ya ek olarak codespace 'e diğer istemcilerle bağlanmayı düşünüyorsanız, belirli özellikleri Visual Studio Code ayarlama yararlı olur. 

* `extensions` -Yüklenmesi gereken [Visual Studio Code Market](https://marketplace.visualstudio.com/vscode) uzantıları dizisi.
* `settings`  -Uygulanacak [Visual Studio Code ayarları](https://code.visualstudio.com/docs/getstarted/settings) kümesi.
* `forwardPorts`-Codespace çalışırken otomatik olarak yerel olarak iletilmesi gereken bağlantı noktası veya bağlantı noktası dizisi.
* `postCreateCommand` -Codespace oluşturulduktan sonra çalıştırılacak komut bağımsız değişkenlerinin bir komut dizesi veya listesi.

> [!NOTE]
> Dosya **devcontainer.js** , [Uzaktan geliştirmeyi](https://code.visualstudio.com/docs/remote/remote-overview)Visual Studio Code desteklemek için de kullanılır ve bu belgede kapsanmayan ek özelliklere sahiptir. Bu ek özellikler dosyaya eklemek güvenlidir, ancak Codespaces tarafından yok sayılır. Daha fazla bilgi için code.visualstudio.com adresindeki [ başvurudevcontainer.js](https://code.visualstudio.com/docs/remote/devcontainerjson-reference) bakın.

## <a name="customize-with-devinit"></a>Devinit ile özelleştirme

[devinit](../../devinit/getting-started-with-devinit.md) , Windows codespaces 'a eklenen ve ortamınıza çerçeveleri ve araçları yüklemenize olanak tanıyan bir komut satırı aracıdır. Bir komut isteminden () el ile çalıştırılabilir, `devinit run -t require-dotnetcoresdk` ancak gerçek güç, bir kod alanını oluşturduğunuz her seferinde bir codespace yapılandırmak için dosyanın özel [ *.devinit.js*](../../devinit/devinit-json.md) oluşturma işleminden gelir.

`devinit` SQL Server ve Azure CLı gibi belirli öğeleri yüklemeye ve ayrıca Chocolatey, NPM ve vcpkg gibi genel paket yöneticilerini çalıştırmaya yönelik bir araç kümesi içerir. Araçların tüm listesini `devinit` [kullanılabilir araçlar](../../devinit/devinit-tool-list.md) belgelerinde bulabilirsiniz.

### <a name="devinitjson"></a>Üzerinde devinit.js

Komut satırını doğrudan çalıştırabilmeniz sırasında, `devinit` çalıştırılacak araçlar kümesini açıklayan yapılandırma dosyalarında [*devinit.js*](../../devinit/devinit-json.md) oluşturmanız önerilir `devinit` . 

Örneğin, [.NET Core SDK](/dotnet/core/sdk)yüklemek için bir *.devinit.js* şu şekilde görünür:

```json
{
    "run": [
        {
            "comments": "We need the .NET Core SDK."
            "tool": "require-dotnetcoresdk"
        }
    ]
}
```

Projenizin kökündeki bir *.devinit.js* yazdığınızda, çalıştırdığınızda kullanılacaktır `devinit init` ... Varsayılan olarak, `devinit.exe` aşağıdaki konumlarda dosyayı arar:

1. *{geçerli-dizin} \\ Üzerinde.devinit.js*
2. *{geçerli-dizin} \\ Üzerinde.devinit\devinit.js*

### <a name="running-devinit-when-creating-a-codespace"></a>Codespace oluştururken devinit çalıştırma

`devinit` `postCreateCommand` Dosyadaki bir *devcontainers.js* özelliğini kullanarak bir Codespace oluşturulduktan sonra, GitHub kod alanları 'nı çalıştırmak için talimat verebilirsiniz. Yukarıda belirtildiği gibi, GitHub Codespaces, codespace veya istemci örneğini özelleştirmek için klonlanan deponuzdaki bir *devcontainer.js* arar ve bu, özellikte açıklanan komutları çalıştırır `postCreateCommand` .

Belirterek `devinit init` , `devinit` yapılandırmada *devinit.js* kullanılarak çalıştırılır.

```json
{
  "postCreateCommand": "devinit init"
}
```

### <a name="an-example"></a>Örnek

.NET Core Entity Framework komut satırı aracını yükleme hakkında basit bir örnek aşağıda verilmiştir `dotnet-ef` .

**devcontainer.json**

Depo kökündeki dosya *.devcontainer.js* içeriği. 

```json
{
  "postCreateCommand": "devinit init"
}
```

**Üzerindedevinit.js**

Dosyadaki *.devinit.js* içeriği. Bu dosyanın *.devcontainer.js* ile aynı klasörde olması gerekir.

```json
{
    "run": [
        {
            "comments": "Install the Entity Framework tools",
            "tool": "dotnet-toolinstall",
            "input": "dotnet-ef",
        }
     ]
}
```

Örnekler listesinde daha fazla `devinit` örnek bulabilirsiniz `devinit` [Samples list](../../devinit/sample-readme.md).

## <a name="port-forwarding"></a>Bağlantı noktası iletme

GitHub Codespaces, bağlantı noktası iletme yoluyla uzak ortamlarda çalışan uygulama ve hizmetlere erişim sağlar. Varsayılan olarak, güvenlik sorunları için hiçbir bağlantı noktası iletilmez. Ancak, belirli bağlantı noktalarını bir codespace içinde açılacak şekilde belirtebilirsiniz.

### <a name="configure-port-forwarding"></a>Bağlantı noktası iletmeyi yapılandırma

Belirli bir depo için varsayılan olarak iletilmesi gereken bir veya daha fazla bağlantı noktası varsa, bu, özelliği ile *üzerindedevcontainer.js* yapılandırılabilir `forwardPorts` .

* `forwardPorts` -Ortam çalışırken otomatik olarak yerel olarak iletilmesi gereken bağlantı noktası veya bağlantı noktası dizisi.

## <a name="installed-software-specifics"></a>Yazılım özellikleri yüklendi

### <a name="microsoft-sql-server"></a>Microsoft SQL Server

Microsoft SQL Server 2019 Express Edition Windows Codespace ortamında kullanılabilir ve yerel hizmet olarak çalışıyor (LocalDB). Uygulamanızın ve Visual Studio terminalinin farklı çalıştığı Geçerli Kullanıcı, SQL Server için SQL yönetici haklarına sahiptir. Sunucuyu yönetmek için, PowerShell 'i Visual Studio terminalinde veya gibi diğer komut satırı araçlarında kullanmanız gerekir `dotnet-ef` . Şu anda SQL Server Management Studio ve diğer uzaktan yönetim araçları kullanılamıyor.

#### <a name="example-connection-string"></a>Örnek bağlantı dizesi

Aşağıda, yerel MS SQL Server 'a bağlanmak için bir bağlantı dizesi örneği verilmiştir.

```csharp
"Server=(LocalDB);Integrated Security=true;"
```

### <a name="azure-cli"></a>Azure CLI’si

Azure CLı, tüm Windows Codespace ortamlarına yüklenir ve farklı yolda bulunabilir `az` .

#### <a name="using-azure-resources"></a>Azure kaynaklarını kullanma

Uygulamanızın kimliğini Azure kaynaklarına karşı doğrulamak için bir Azure Active Directory kimliği kullanıyorsanız, ilk olarak Visual Studio terminalinde Azure 'da oturum açmanız gerekecektir. Oturum açmak için Azure CLı `login` komutunu cihaz oturum açma akışında (aşağıdaki örnekte gösterildiği gibi) kullanın. Oturum açıldıktan sonra, uygulamanız ve Terminal oturumunuz bu kimliği kullanabilmelidir.

```powershell
> az login --use-device-code
```

`az login`Azure CLI [belgelerindeki](/cli/azure/reference-index#az_login)komutla ilgili daha fazla bilgi edinebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [GitHub Codespaces nedir?](codespaces-overview.md)
- [Visual Studio 'Yu bir codespace ile kullanma](use-visual-studio-with-codespaces.md)