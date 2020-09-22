---
title: Sık Sorulan Sorular
description: Devinit aracı hakkında sık sorulan sorular.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 2b482de4dd6c72aa744ef92563b8c1f23febbdd1
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005006"
---
# <a name="frequently-asked-questions-for-devinit"></a>Devinit için sık sorulan sorular

## <a name="is-devinit-just-for-github-codespaces"></a>Yalnızca GitHub Codespaces için devinit mi?

Şimdilik, devinit yalnızca GitHub Codespaces özel beta 'nın bir parçası olarak kullanılabilir. Ancak, Visual Studio 2019 ' nin gelecek bir sürümünde devinit 'yi dahil etmek için planlıyoruz.

## <a name="is-it-windows-only"></a>Yalnızca Windows mu?
Evet, devinit, Visual Studio kullanan geliştiriciler için çalışan geliştirici ortamları oluşturmaya odaklanmıştır, yani Windows. Diğer platformları göz önünde bulunduruyoruz, ancak çoğu, Visual Studio ve Windows ile başlamak istememiz için harika çözümler sunuyor.

## <a name="theres-no-tool-for-the-dependency-i-need"></a>Gerekli olan bağımlılığa yönelik bir araç yok!

Ne yazık ki! GitHub Codespaces özel beta kısmında çalışıyorsanız, özel beta için geri bildirim kanalı üzerinden bize geri dönebilirsiniz. Özel Beta 'nın bir parçası değilseniz, ihtiyacınız olan bilgilerle ilgili geri bildirimlerinizi hala sevtireceğiz ve ihtiyacınız olan araç için destek istemek üzere etikete sahip [Visual Studio](https://github.com/MicrosoftDocs/visualstudio-docs/) Belgelerimizde bir sorun da oluşturabilirsiniz `devinit` .

## <a name="something-went-wrong-how-do-i-debug"></a>Bir sorun oluştu, nasıl hata ayıklaması yapabilirim?

Devınit başarısız olursa, deneyebileceğiniz ilk şey `--verbose / -v` daha fazla bilgi almak için olan bayraktır. Devınit 'in çağrıldığı temel alınan araç bir sorunla karşılaşıyor. Ayrıntılı günlük bilgileri, ileri bakabileceğiniz bir Clue içermelidir.

## <a name="why-not-just-a-script"></a>Neden yalnızca bir betik değil?

Ortamları bir komut dosyası aracılığıyla ayarlamak bir zaman eski tekniktir ve harika bir şekilde çalışabilir. Sizin için çalışıyorsa, şunu kullanın! devinit, geliştiricilerin betikler için en iyi seçenek olmadığı durumlarda başka bir seçenektir.

## <a name="why-not-a-container"></a>Neden bir kapsayıcı değil?

Kapsayıcılar ve Docker, kod aracılığıyla bir ortamı dağıtmaya yönelik harika araçlardır. Kapsayıcıların sizin için doğru çözüm olmasının birkaç nedeni vardır:

1. Windows Masaüstü tabanlı bir geliştirme ortamı kullanmak istiyorsanız.
1. Zaten bir işletim sistemi varsa ve yeni bir ortam dağıtmak yerine yalnızca ince ayar istiyorsanız.

Bu nedenlerden dolayı devinit, şu anda sahip olduğunuz Windows ortamını özelleştirmeye yöneliktir.

## <a name="what-about-other-vm-creation-tools-for-example-terraform-packer-chef-vagrant-etc"></a>Diğer VM oluşturma araçları (örneğin, Terkform, Packer, Chef, vagrant, vb.)

Windows görüntülerini oluşturmaya yönelik çok sayıda harika araç vardır ve bunları kullanmanız gerekir! Ancak, aklımız tüm senaryoları karşıladığımız bir tane bulunamadı. Devınit 'in, geliştiricilerin ortamlarını belirli bir depoda gerekli olan her türlü şekilde özelleştirmesini ve VM görüntülerini oluşturmaya yönelik bir araç olması yerine Visual Studio ile harika bir tümleştirme sahibi olmasını istiyoruz.

## <a name="what-about-winget"></a>Winget hakkında ne var?

devinit, Winget gibi bir paket yöneticisi değildir ve bunun olmasını istemiyorum. Devinit ile Winget kullanabilmek istiyoruz ve yalnızca bunun için bir araç üzerinde çalışıyoruz.

## <a name="how-are-restarts-handled"></a>Yeniden başlatmalar nasıl işlenir?

Devinit 'nin yüklediği herhangi bir şey işletim sisteminin yeniden başlatılmasını gerektiriyorsa, konsola bir hata mesajı gönderilir. Daha sonra işletim sistemini size uygun bir zamanda yeniden başlatmanız gerekir. Yeniden başlatıldıktan sonra, tüm bağımlılıklar yüklü değilse devinit yeniden çalıştırmanız gerekebilir.

## <a name="working-with-others"></a>Başkalarıyla çalışma

devinit, uygulamanızın sahip olabileceği bağımlılıkları dağıtmak ve yapılandırmak için bir çok geniş ekosistemin kullanımını etkinleştirmeye yönelik olarak tasarlanmıştır. Devınit 'in sunduğu özellikler hakkında bir düşünme karşın devinit, genellikle diğer araçların bildirim temelli bir JSON dosyasından yürütülmesini sağlar.

Bugün, devinit yalnızca Başlarken ve [araç listemiz](devinit-tool-list.md) yalnızca bir başlangıç.
