---
title: Komut satırı anahtarları ekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e28a3f303849458a407b212d3aad1a8c198f6d25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62562282"
---
# <a name="adding-command-line-switches"></a>Komut Satırı Anahtarları Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

devenv.exe yürütüldüğünde VSPackage için uygulanan komut satırı anahtarlarını ekleyebilirsiniz. <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute>Anahtarın adını ve özelliklerini bildirmek için kullanın. Bu örnekte, bir bağımsız **değişken içermeyen ve** VSPackage otomatik olarak yüklenen VSPackage adlı VSPackage alt sınıfı Için mySwitch anahtarı eklenir.  
  
```csharp  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 Adlandırılmış parametreler aşağıdaki tabloda gösterilmiştir  
  
 Arguments  
 Anahtar için bağımsız değişkenlerin sayısı. "*" Veya bağımsız değişken listesi olabilir.  
  
 Isteğsiz yük  
 Bu 1 olarak ayarlanırsa VSPackage 'ı otomatik olarak yükleyin, aksi takdirde 0 olarak ayarlayın.  
  
 HelpString  
 **Devenv/?** ile görüntülenecek dizenin Yardım dizesi veya kaynak kimliği.  
  
 Name  
 Anahtar.  
  
 PackageGuid  
 Paketin GUID 'SI.  
  
 Bağımsız değişkenlerin ilk değeri genellikle 0 veya 1 ' dir. Komut satırının tüm geri kalanın bağımsız değişken olduğunu göstermek için ' * ' özel değeri kullanılabilir. Bu, kullanıcının bir hata ayıklayıcı komut dizesinde geçmesi gereken hata ayıklama senaryolarında yararlı olabilir.  
  
 Kullanılan yük değeri `true` (1) ya da `false` (0) VSPackage 'ın otomatik olarak yüklenmesi gerektiğini gösterir.  
  
 HelpString değeri, devenv/? içinde görüntülenen dizenin kaynak KIMLIĞIDIR. Yardım görüntüleme. Bu değer, nnn ' in bir tamsayı olduğu "#nnn" biçiminde olmalıdır. Kaynak dosyasındaki dize değeri yeni bir satır karakteriyle bitmelidir.  
  
 Ad değeri, anahtarın adıdır.  
  
 PackageGuid değeri, bu anahtarı uygulayan paketin GUID 'sidir. IDE, komut satırı anahtarının uygulandığı kayıt defterindeki VSPackage 'ı bulmak için bu GUID 'yi kullanır.  
  
## <a name="retrieving-command-line-switches"></a>Komut satırı anahtarlarını alma  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Devenv komut satırı anahtarları](../ide/reference/devenv-command-line-switches.md)   
 [CreatePkgDef yardımcı programı](../extensibility/internals/createpkgdef-utility.md)   
 [.Pkgdef Dosyaları](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
