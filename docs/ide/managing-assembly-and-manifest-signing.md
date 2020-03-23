---
title: Derleme ve bildirim imzalamayı yönetme
ms.date: 02/17/2017
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 6c1ef36b-25f7-4ad0-b29a-51801b7a5420
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f13df00059523ca87e720a999c596e203b20e49
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593687"
---
# <a name="manage-assembly-and-manifest-signing"></a>Derleme ve bildirim imzalamayı yönetme

Güçlü ad imzalama, yazılım bileşenine genel olarak benzersiz bir kimlik verir. Derlemenin başka biri tarafından taklit edilemeyeceğini garanti etmek ve bileşen bağımlılıklarının ve yapılandırma deyimlerinin doğru bileşen ve bileşen sürümüyle eşlediğinden emin olmak için güçlü adlar kullanılır.

Güçlü bir ad, derlemenin kimliğini (basit metin adı, sürüm numarası ve kültür bilgileri) ve ortak anahtar belirteci ve dijital imzadan oluşur.

Visual Basic ve C# projelerinde derlemeleri imzalama hakkında daha fazla bilgi için [bkz.](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies)

C++ projelerinde derlemeleri imzalama hakkında daha fazla bilgi için Bkz. [Güçlü adlandırılmış derlemeler (C++/CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli).

> [!NOTE]
> Güçlü isim imzalama, derlemenin ters mühendisliğine karşı koruma sağlamaz. Ters mühendislik karşı korumak için, [Dotfuscator Topluluk](dotfuscator/index.md)bakın.

## <a name="asset-types-and-signing"></a>Varlık türleri ve imzalama

.NET derlemelerini ve uygulama bildirimlerini imzalayabilirsiniz:

- Yürütülebilir (*.exe*)

- Uygulama bildirimleri (*.exe.manifest*)

- Dağıtım bildirimleri (*.application*)

- Paylaşılan bileşen derlemeleri (*.dll*)

Aşağıdaki varlık türlerini imzalayın:

1. Derlemeler, bunları genel derleme önbelleğine (GAC) dağıtmak istiyorsanız.

2. ClickOnce uygulama ve dağıtım bildirimleri. Visual Studio, bu uygulamalar için varsayılan olarak imzalamayı sağlar.

3. COM birlikte çalışabilirliği için kullanılan birincil interop montajları. TLBIMP yardımcı programı, COM türü kitaplığından birincil interop derlemesi oluştururken güçlü adlandırmayı zorlar.

Genel olarak, yürütülebilir leri imzalamamalısınız. Güçlü bir şekilde adlandırılmış bir bileşen, uygulamayla birlikte dağıtılan güçlü adlandırılmış olmayan bir bileşene başvuruyapamaz. Visual Studio uygulama yürütülebilirleri imzalamaz, bunun yerine zayıf adlandırılmış yürütülebilir işaret uygulama bildirimini imzalar. İmzalama bağımlılıkları yönetmeyi zorlaştırabileceğinden, uygulamanız için özel olan bileşenleri imzalamaktan kaçının.

## <a name="how-to-sign-an-assembly-in-visual-studio"></a>Visual Studio'da montaj nasıl imzaatılır?

Proje özellikleri penceresinin **İmzalama** sekmesini kullanarak bir uygulamayı veya bileşeni imzalarsınız **(Çözüm Gezgini'nde** proje düğümüne sağ tıklayın ve **Özellikler'i**seçin). **İmza** sekmesini seçin ve ardından montaj onay kutusunu **imzala'yı** seçin.

Anahtar dosyası belirtin. Yeni bir anahtar dosyası oluşturmayı seçerseniz, yeni anahtar dosyaları her zaman *.pfx* biçiminde oluşturulur. Yeni dosya için bir ad ve parola gerekir.

> [!WARNING]
> Başka birinin kullanmasını önlemek için anahtar dosyanızı her zaman bir parolayla korumanız gerekir. Ayrıca, sağlayıcıları veya sertifika depolarını kullanarak anahtarlarınızı da güvene alabilirsiniz.

Ayrıca, önceden oluşturduğunuz bir anahtarı da işaret edebilirsiniz. Anahtar oluşturma hakkında daha fazla bilgi için [bkz.](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair)

Yalnızca ortak bir anahtara erişiminiz varsa, anahtarı atamayı ertelemek için gecikme imzalamayı kullanabilirsiniz. **Yalnızca Gecikme işareti onay** kutusunu seçerek erteleme imzalamayı etkinleştirirsiniz. Gecikme imzalı bir proje çalışmaz ve hata ayıklama yapamazsınız. Ancak, `-Vr` seçenek ile [Sn.exe güçlü ad aracını](/dotnet/framework/tools/sn-exe-strong-name-tool) kullanarak geliştirme sırasında doğrulama atlayabilirsiniz.

İmzalama bildirimleri hakkında bilgi için [bkz: Uygulama ve dağıtım bildirimlerini imzalayın.](../ide/how-to-sign-application-and-deployment-manifests.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Güçlü adlandırılmış derlemeler](/dotnet/framework/app-domains/strong-named-assemblies)
- [Güçlü adlandırılmış derlemeler (C++/CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli)
