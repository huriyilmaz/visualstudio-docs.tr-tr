---
title: Dia2dump örneği | Microsoft Docs
ms.date: 07/24/2018
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17fe6d65e70399ccac5b9ef4e2f1234ef4e3698e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468688"
---
# <a name="dia2dump-sample"></a>Dia2dump Örneği

Dia2dump örnek, Microsoft hata ayıklama arabirimi erişim yazılım geliştirme seti 'nin (DIA SDK) bilgi için bir PDB dosyasını sorgulamak için nasıl kullanılacağını gösterir.

Dia2dump örneği, Visual Studio ile birlikte yüklenir ve çözümü ve kaynak dosyalarını içerir. Derlenmiş yürütülebilir dosya komut satırından çalışır. Tüm program veritabanı (. pdb) dosyasının veya ilgilendiğiniz bölümlerin içeriğini gösterebilir.

## <a name="install-the-sample"></a>Örneği yükler

Örnek, Visual Studio Yükleyicisi C++ iş yüküne **sahip masaüstü geliştirmeyi** seçtiğinizde yüklenir. Visual Studio 'Yu yüklemek ve belirli iş yüklerini ve bireysel bileşenleri seçmek hakkında daha fazla bilgi için bkz. [Visual Studio 'Yu yüklemek](../../install/install-visual-studio.md).

Yüklendiğinde, örnek Visual Studio yükleme dizininizde, \DIA Sdk\samples\dia2dumpadlı bir alt dizinde bulunur.

## <a name="build-the-sample"></a>Örneği oluşturma

Varsayılan olarak, yükleme dizini korumalı bir dizindir. Diğer bir deyişle, bu konumda örnek çözümü derlemek ve düzenlemek için yükseltilmiş bir geliştirici komut istemi veya Visual Studio örneği kullanmanız gerekir. Derlemeyi basitleştirmek için, önce dosyaları örnek dizinden belgeler klasörünüzdeki bir klasör gibi başka bir dizine kopyalamanız ve sonra örneği oluşturmanız önerilir.

### <a name="to-build-the-dia2dump-sample-in-visual-studio"></a>Visual Studio 'da Dia2Dump örneği oluşturmak için

1. Visual Studio 'da DIA2Dump. sln dosyasını açın. Çözümü başka bir dizine kopyalamadıysanız, Visual Studio 'Yu yükseltilmiş izinlerle yeniden başlatmanız istenebilir.

1. **Çözüm Gezgini**, Dia2Dump projesini seçin (çözümü değil).

1. Projenin **Özellik sayfaları** iletişim kutusunu açın. Ayrıntılar için bkz. [Proje özellikleriyle çalışma](/cpp/build/working-with-project-properties).

1. **Yapılandırma özellikleri**  >  **C/C++**  >  **genel** özellik sayfasını açın.

1. **Ek Içerme dizinleri** özelliğinde, açılan denetimi seçin ve ardından **Düzenle**' yi seçin.

1. **Ek Içerik dizinleri** iletişim kutusunda, Düzenle alanına, `$(VSInstallDir)DIA SDK\include` dizini girin. Derleyicinin dia2. h dosyasını bulabileceği garantilemek için bu dizini ekleyin. Değişikliklerinizi kaydetmek için **Tamam ' ı** seçin.

1. Değişikliklerinizi proje özelliklerine kaydetmek için **Tamam ' ı** seçin.

1. **Derle** menüsünde **çözümü yeniden derle**' yi seçin. Varsayılan olarak, Visual Studio, çözüm dizininin bir hata ayıklama alt dizininde bulunan örneğin bir hata ayıklama sürümü oluşturur.

1. Visual Studio’yu kapatın.

### <a name="to-build-the-dia2dump-sample-at-the-command-line"></a>Komut satırında Dia2Dump örneğini oluşturmak için

1. Geliştirici komut istemi penceresinde, örnek dosyaları kopyaladığınız dizine geçin. Örneği başka bir dizine kopyalamadıysanız yükseltilmiş (yönetici olarak çalıştır) Geliştirici komut istemi penceresi kullanmanız gerekir.

1. `nmake makefile`dia2dump.exe varsayılan hata ayıklama yapılandırmasını derlemek için komutunu girin.

## <a name="run-the-dia2dump-sample"></a>Dia2Dump örneğini çalıştırma

Dia2Dump.exe, hizmetlerini sağlamak için msçya*Version*. dll com sunucusuna bağımlıdır. Visual Studio 2015 ' den başlayarak sürüm msdia140.dll. MSDIA*sürümü*. dll com sunucusu başlatılmazsa, dia2dump.exe çalışmadan önce kaydetmelisiniz. DIA SDK dizininde DLL 'nin x86 sürümünü içeren bir bin alt dizini vardır. X64 mimari makineler için bir sürüm, bin\amd64 ' te ve ARM için bir sürüm de bin\arm. Dll 'yi kaydetmek için, yükseltilmiş bir geliştirici komut istemi penceresi açın ve makine mimarinizin sürümünü içeren dizine geçin. `regsvr32 msdia140.dll`Com sunucusunu kaydetmek için komutunu girin.

### <a name="to-run-the-sample"></a>Örnek çalıştırmak için

1. Bir komut istemi açın ve derlediniz dia2dump.exe içeren dizine geçin.

1. `dia2dump filename` *Dosya adının* , incelenecek bir pdb dosyasının adı olduğu komutu girin. PDB dosyası başka bir dizinse dosya *adı*olarak dosyanın tam yolunu kullanın. Bu komut PDB dosyasındaki tüm verileri listeler.

1. Dia2Dump yalnızca seçilen bilgileri görüntülemeye yönelik başka seçeneklere sahiptir. `dia2dump -?`Tüm kullanılabilir seçenekleri listelemek için komutunu kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio projelerini bağlantı noktası, geçirme ve yükseltme](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)
