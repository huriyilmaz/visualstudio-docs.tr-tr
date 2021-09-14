---
title: Command-Line anahtarları ekleme | Microsoft Docs
description: devenv.exe komutu yürütüldüğünde VSPackage 'a uygulanan komut satırı anahtarlarının nasıl ekleneceğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 539ab9c7a70d1e2ed22c864132048175eebfcda3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635257"
---
# <a name="add-command-line-switches"></a>Komut satırı anahtarları Ekle
*devenv.exe* yürütüldüğünde VSPackage için uygulanan komut satırı anahtarlarını ekleyebilirsiniz. <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute>Anahtarın adını ve özelliklerini bildirmek için kullanın. Bu örnekte, bir bağımsız **değişken içermeyen ve** VSPackage otomatik olarak yüklenen VSPackage adlı VSPackage alt sınıfı Için mySwitch anahtarı eklenir.

```csharp
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]
```

 Adlandırılmış parametreler aşağıdaki açıklamalarda gösterilmiştir.

|Ad|Açıklama|
|-|-|
| Bağımsız değişkenler | Anahtar için bağımsız değişkenlerin sayısı. "*" Veya bağımsız değişken listesi olabilir. |
| Isteğsiz yük | Bu 1 olarak ayarlanırsa VSPackage 'ı otomatik olarak yükleyin, aksi takdirde 0 olarak ayarlayın. |
| HelpString | **Devenv/?** ile görüntülenecek dizenin Yardım dizesi veya kaynak kimliği. |
| Name | Anahtar. |
| PackageGuid | Paketin GUID 'SI. |

 Bağımsız değişkenlerin ilk değeri genellikle 0 veya 1 ' dir. Komut satırının tüm geri kalanın bağımsız değişken olduğunu göstermek için ' * ' özel değeri kullanılabilir. Bu, kullanıcının bir hata ayıklayıcı komut dizesinde geçmesi gereken hata ayıklama senaryolarında yararlı olabilir.

 Kullanılan yük değeri `true` (1) ya da `false` (0) VSPackage 'ın otomatik olarak yüklenmesi gerektiğini gösterir.

 HelpString değeri, **devenv/?** içinde görüntülenen DIZENIN kaynak kimliğidir. Yardım görüntüleme. Bu değer, nnn ' in bir tamsayı olduğu "#nnn" biçiminde olmalıdır. Kaynak dosyasındaki dize değeri yeni bir satır karakteriyle bitmelidir.

 Ad değeri, anahtarın adıdır.

 PackageGuid değeri, bu anahtarı uygulayan paketin GUID 'sidir. IDE, komut satırı anahtarının uygulandığı kayıt defterindeki VSPackage 'ı bulmak için bu GUID 'yi kullanır.

## <a name="retrieve-command-line-switches"></a>Komut satırı anahtarlarını alma
 Paketiniz yüklendiğinde, aşağıdaki adımları tamamlayarak komut satırı anahtarlarını alabilirsiniz.

1. VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> uygulamanızda, `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> arabirimini almak için öğesini çağırın <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> .

2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A>Kullanıcının girdiği komut satırı anahtarlarını almak için çağırın.

   Aşağıdaki kod, MySwitch komut satırı anahtarının Kullanıcı tarafından girilip girilmediğini nasıl bulacağınızı göstermektedir:

```csharp
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));

int isPresent = 0;
string optionValue = "";

cmdline.GetOption("MySwitch", out isPresent, out optionValue);
```

 Paketinizin her yüklenilişinde komut satırı anahtarlarınızın denetlenmesi sizin sorumluluğunuzdadır.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- [Devenv komut satırı anahtarları](../ide/reference/devenv-command-line-switches.md)
- [CreatePkgDef yardımcı programı](../extensibility/internals/createpkgdef-utility.md)
- [. Pkgdef dosyaları](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/)
