---
title: Visual Studio açık klasör genişletilebilirliği genel bakış | Microsoft Docs
ms.date: 02/21/2018
ms.topic: overview
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: d213a7add358c46f7088f504d8c54352cda44a1c
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905973"
---
# <a name="open-folder-extensibility"></a>Açık klasör genişletilebilirliği

[Klasörü aç](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) özelliği, kullanıcıların proje veya çözüm dosyalarına gerek duymadan Visual Studio 'da herhangi bir kod temeli açmasına olanak sağlar. Klasörü aç özelliği, kullanıcıların Visual Studio 'dan beklediği özellikleri sağlar; örneğin:

* Çözüm Gezgini tümleştirme ve arama
* Düzenleyici renklendirme
* Gezintiye git
* Dosyalarda bul arama

.NET ve C++ geliştirme gibi Iş yükleri ile birlikte kullanıldığında, kullanıcılar şunları da alabilirler:

* Zengin IntelliSense
* Dile özgü işlevsellik

Açık klasör ile, uzantı yazarları herhangi bir dil için zengin özellikler oluşturabilir. Kullanıcının kod tabanında herhangi bir dosya için oluşturma, hata ayıklama ve simge aramasını destekleyen API 'Ler vardır. Geçerli Extender 'lar, proje veya çözüm yedeklemesi olmadan kodu anlamak için mevcut Visual Studio özelliklerini güncelleştirebilir.

## <a name="an-api-without-project-systems"></a>Proje sistemleri olmayan bir API

Tarihsel olarak, Visual Studio yalnızca bir çözümdeki dosyaları ve proje sistemlerini kullanarak projelerini anladı. Proje sistemi, yüklü bir projenin işlevlerinden ve Kullanıcı etkileşimlerinden sorumludur. Projenin içerdiği dosyaları, proje içeriklerinin görsel gösterimini, diğer projelerdeki bağımlılıkları ve temel alınan proje dosyasının değiştirilmesini anlamıştır. Diğer bileşenlerin Kullanıcı adına çalıştığı bu hiyerarşiler ve yetenekler vardır. Tüm kod tabanları bir proje ve çözüm yapısında iyi temsil edilmez. Linux için C++ dilinde yazılmış komut dosyası dilleri ve açık kaynak kodu iyi örneklerdir. Açık klasör sayesinde, Visual Studio kullanıcılara kaynak kodla etkileşim kurmak için yeni bir yol sağlar.

Açık klasör API 'Leri `Microsoft.VisualStudio.Workspace.*` ad alanı altındadır ve Extender 'lar tarafından, açık klasör içindeki dosyaların etrafında veri veya eylem oluşturmak ve bunları kullanmak için kullanılabilir. Uzantılar, bu API 'Leri aşağıdakiler dahil olmak üzere birçok alana işlevsellik sağlamak için kullanabilir:

- [Çalışma alanları](workspaces.md) -açık klasör genişletilebilirliği başlangıç noktası, çalışma alanı ve API 'sdır.
- Dosya [bağlamları ve eylemler](workspace-file-contexts.md) -dosya bağlamları aracılığıyla belirtilen dosya özel kod zekası.
- [Dizin oluşturma](workspace-indexing.md) -açık klasör çalışma alanlarıyla ilgili verileri toplayın ve kalıcı hale getirin.
- [Dil Hizmetleri](workspace-language-services.md) -dil hizmetlerini açık klasör çalışma alanlarıyla tümleştirin.
- Açık klasör çalışma alanları için [derleme](workspace-build.md) oluşturma desteği.

Aşağıdaki türleri kullanan özelliklerin, açık klasörü desteklemek için yeni API 'Leri benimsemeniz gerekecektir:

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>Geri bildirim, açıklamalar, sorunlar

Klasörü açın ve `Microsoft.VisualStudio.Workspace.*` API 'ler etkin geliştirme aşamasındadır. Beklenmeyen davranışlar görürseniz, ilgilendiğiniz yayın için bilinen sorunlara bakın. [Geliştirici topluluğu](https://developercommunity.visualstudio.com) , oylamak ve sorun oluşturmak için önerilen yerdir. Her geri bildirimde, sorununuzun ayrıntılı bir açıklamasını kesinlikle öneririz. Geliştirmekte olduğunuz Visual Studio sürümünü, kullandığınız API 'Leri (her ikisi de ne uyguladığınızı, ne ile etkileşimde bulundudığınızı), beklenen sonucu ve gerçek sonucu dahil edin. Mümkünse devenv.exe işlemin bir dökümünü ekleyin. Bu ve ilgili belgelerde geri bildirimde bulunmak için GitHub 'ın sorun izlemesini kullanın.

## <a name="next-steps"></a>Sonraki adımlar

* [Çalışma alanları](workspaces.md) -açık klasör çalışma alanı API 'si hakkında bilgi edinin.