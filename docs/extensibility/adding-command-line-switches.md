---
title: Komut Satırı Anahtarları Ekleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f2df3a704c34d97c9d5acfa72249fe492b7f812
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740172"
---
# <a name="add-command-line-switches"></a>Komut satırı anahtarları ekleme
*Devenv.exe* yürütüldüğünde VSPackage'ınıza uygulanan komut satırı anahtarlarını ekleyebilirsiniz. Anahtarın adını ve özelliklerini bildirmek için kullanın. <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> Bu örnekte, MySwitch anahtarı, bağımsız değişken olmadan ve VSPackage otomatik olarak yüklenmiş olan **AddCommandSwitchPackage** adlı VSPackage alt sınıfı için eklenir.

```csharp
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]
```

 Adlandırılmış parametreler aşağıdaki açıklamalarda gösterilmiştir.

||||
|-|-|-|-|
| Parametre | Açıklama|
| Bağımsız Değişkenler | Geçiş için bağımsız değişken sayısı. "*" veya bağımsız değişkenlistesi olabilir. |
| DemandLoad | VsPackage'ı 1 olarak ayarlanmışsa, aksi takdirde 0 olarak ayarlanırsa otomatik olarak yükleyin. |
| Helpstring | **Devenv**ile görüntülenecek dize yardım dizesi veya kaynak kimliği /? . |
| Adı | Anahtar. |
| PaketGuid | Paketin GUID'i. |

 Bağımsız değişkenlerin ilk değeri genellikle 0 veya 1'dir. Komut satırının geri kalanının bağımsız değişken olduğunu belirtmek için '*' özel bir değeri kullanılabilir. Bu, kullanıcının hata ayıklama komut dizesinde geçmesi gereken senaryoları hata ayıklamak için yararlı olabilir.

 DemandLoad değeri `true` (1) veya `false` (0) VSPackage'ın otomatik olarak yüklenmesi gerektiğini gösterir.

 HelpString değeri **devenv /?** Görüntülenmesine yardımcı olun. Bu değer, nnn bir tamsayı olduğu "#nnn" şeklinde olmalıdır. Kaynak dosyasındaki dize değeri yeni bir satır karakteriyle sona ermelidir.

 Ad değeri anahtarın adıdır.

 PackageGuid değeri, bu anahtarı uygulayan paketin GUID değeridir. IDE, komut satırı anahtarının uygulandığı kayıt defterinde VSPackage'ı bulmak için bu GUID'i kullanır.

## <a name="retrieve-command-line-switches"></a>Komut satırı anahtarlarını al
 Paketiniz yüklendiğinde, aşağıdaki adımları tamamlayarak komut satırı anahtarlarını alabilirsiniz.

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> VSPackage'ınızın uygulamasında arayüz `QueryService` almak <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> için <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> çağrıda bulunuyorum.

2. Kullanıcının girdiği komut satırı anahtarlarını almak için arayın. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A>

   Aşağıdaki kod, MySwitch komut satırı anahtarının kullanıcı tarafından girilip girmediğini nasıl öğrenilir:

```csharp
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));

int isPresent = 0;
string optionValue = "";

cmdline.GetOption("MySwitch", out isPresent, out optionValue);
```

 Paketiniz her yüklendiğinde komut satırı anahtarlarınızı kontrol etmek sizin sorumluluğunuzdadır.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- [Devenv komut satırı anahtarları](../ide/reference/devenv-command-line-switches.md)
- [CreatePkgDef yardımcı programı](../extensibility/internals/createpkgdef-utility.md)
- [. Pkgdef dosyaları](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/)
