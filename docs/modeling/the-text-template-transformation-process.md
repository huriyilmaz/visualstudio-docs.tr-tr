---
title: Metin Şablonu Dönüştürme Süreci
description: Metin şablonu dönüştürme işleminin giriş olarak bir metin şablonu dosyası alır ve çıkış olarak yeni bir metin dosyası oluşturur.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, transformation process
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 37bac2bc17e75dfb9c51bd5611706346c5cca154
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637302"
---
# <a name="the-text-template-transformation-process"></a>Metin Şablonu Dönüştürme Süreci
Metin şablonu dönüştürme işlemi, giriş olarak bir metin şablonu dosyası alır ve çıkış olarak yeni bir metin dosyası oluşturur. Örneğin, metin şablonlarını kullanarak Visual Basic veya C# kodu oluşturabilir veya bir HTML raporu oluşturabilirsiniz.

 Bu süreçte üç bileşen yer alır: altyapı, konak ve yönerge işlemcileri. Altyapı işlemi kontrol eder; çıkış dosyasını üretmek için ana bilgisayar ve yönerge işlemcisi ile etkileşime gelir. Konak, dosyaları ve derlemeleri bulma gibi ortamla herhangi bir etkileşim sağlar. Yönerge işlemcisi, bir XML dosyasından veya veritabanından veri okuma gibi işlevler ekler.

 Metin şablonu dönüştürme işlemi iki adımda gerçekleştirilir. İlk olarak altyapı, oluşturulan dönüştürme sınıfı olarak bilinen geçici bir sınıf oluşturur. Bu sınıf, yönergeleri ve denetim blokları tarafından oluşturulan kodu içerir. Bundan sonra altyapı, çıktı dosyasını üretmek için oluşturulan dönüştürme sınıfını derler ve yürütür.

## <a name="components"></a>Bileşenler

|Bileşen|Açıklama|Özelleştirilebilir (Evet/Hayır)|
|-|-|-|
|Altyapı|Altyapı bileşeni metin şablonu dönüştürme işlemini kontrol eder|Hayır.|
|Host|Konak, altyapı ile kullanıcı ortamı arasındaki arabirimdir. Visual Studio, metin dönüştürme işleminin bir ana bilgisayarıdır.|Evet. Özel bir konak yazabilir.|
|Yönerge İşlemcileri|Yönerge işlemcileri, metin şablonlarında yönergelerini işleyici sınıflardır. Giriş kaynağından metin şablonuna veri sağlamak için yönergeleri kullanabilirsiniz.|Evet. Özel yönerge işlemcileri yazabilir|

## <a name="the-engine"></a>Altyapı
 Altyapı, şablonu konaktan bir dize olarak alır ve bu da dönüştürme sürecinde kullanılan tüm dosyaları işler. Altyapı daha sonra konaklardan özel yönerge işlemcilerini ve ortamın diğer yönlerini bulmasını isterse. Altyapı daha sonra oluşturulan dönüştürme sınıfını derler ve çalıştırır. Altyapı, oluşturulan metni normalde bir dosyaya kaydeden ana bilgisayar için döndürür.

## <a name="the-host"></a>Konak
 Konak, aşağıdakiler de dahil olmak üzere dönüştürme işleminin dışındaki ortamla ilgili her şeyden sorumludur:

- Altyapı veya yönerge işlemcisi tarafından istenen metin ve ikili dosyaları bulma. Konak, derlemeleri bulmak için dizinleri ve genel derleme önbelleğini arayabilir. Konak, altyapı için özel yönerge işlemci kodunu bulur. Konak ayrıca metin dosyalarını bulup okuyabilir ve içeriklerini dize olarak iade ediyor olabilir.

- Altyapı tarafından oluşturulan dönüştürme sınıfını oluşturmak için kullanılan standart derlemelerin ve ad alanlarının listelerini sağlama.

- Altyapı derleyene ve oluşturulan dönüştürme sınıfını yürütürken kullanılan uygulama etki alanını sağlama. Konak uygulamayı şablon kodundaki hatalardan korumak için ayrı bir uygulama etki alanı kullanılır.

- Oluşturulan çıkış dosyasını yazma.

- Oluşturulan çıkış dosyası için varsayılan uzantıyı ayarlama.

- Metin şablonu dönüştürme hatalarını işleme. Örneğin, konak hataları kullanıcı arabiriminde görüntüleniyor veya bir dosyaya yazabilir. (Visual Studio Hata İletisi Penceresinde hatalar görüntülenir.)

- Kullanıcı bir değer sağlamadan yönerge çağırdı ise gerekli parametre değerini sağlama. Yönerge işlemcisi, yönergenin adını ve parametresini belirterek ana bilgisayardan varsa varsayılan bir değer sağlamalarını sorabilir.

## <a name="directives-and-directive-processors"></a>Yönergeler ve Yönerge İşlemcileri
 Yönerge, metin şablonunda yer alan bir komutdur. Oluşturma işlemi için parametreler sağlar. Yönergeler genellikle modelin veya diğer girişin kaynağını ve türünü ve çıktı dosyasının dosya adı uzantısını tanımlar.

 Yönerge işlemcisi bir veya daha fazla yönergeyi işleyene kadar devam ediyor olabilir. Bir şablonu dönüştürdükten sonra, şablonunda yönergeleriyle ilgilenen bir yönerge işlemcisi yüklemişsinizdir.

 Yönergeler, oluşturulan dönüştürme sınıfına kod ekleyerek çalışır. Yönergeleri bir metin şablonundan çağırabilirsiniz ve altyapı, oluşturulan dönüştürme sınıfını oluşturduğunda tüm yönerge çağrılarını işler. Bir yönergeyi başarıyla çağırdikten sonra, metin şablonunuzda yazarak kodun geri kalanı yönergenin sağladığı işlevlere güvenebilirsiniz. Örneğin, şablonunda yönergesine aşağıdaki `import` çağrıyı yapabilirsiniz:

 `<#@ import namespace="System.Text" #>`

 Standart yönerge işlemcisi bunu oluşturulan dönüştürme `using` sınıfındaki bir deyimine dönüştürür. Daha sonra sınıfını `StringBuilder` şablon kodunuzun geri kalanında olarak nitelendirmeden kullanabilirsiniz. `System.Text.StringBuilder`
