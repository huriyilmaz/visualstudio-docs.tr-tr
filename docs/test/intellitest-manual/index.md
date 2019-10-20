---
title: IntelliTest başvurusu el Ile | Microsoft Geliştirici testi araçları
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest Reference Manual, IntelliTest
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 97b28c2810b59465c6d5ac682e95e25b324a95a0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653198"
---
# <a name="intellitest-reference-manual"></a>IntelliTest başvurusu el Ile

## <a name="contents"></a>İçindekiler

* **[IntelliTest 'e genel bakış](introduction.md)**
  - [IntelliTest Merhaba Dünya](introduction.md#the-hello-world-of-intellitest)
  - [Sınırlamalar](introduction.md#limitations)
    * [Belirleyici olmayan ISM](introduction.md#nondeterminism)
    * [Eşzamanlılık](introduction.md#concurrency)
    * [Yerel kod](introduction.md#native-code)
    * [Platformunun](introduction.md#platform)
    * [Dil](introduction.md#language)
    * [Sembolik mantık yürütme](introduction.md#symbolic-reasoning)
    * [Hatalı yığın izlemeleri](introduction.md#incorrect-stack-traces)
  - [Daha fazla okuma](introduction.md#further-reading)

* **[IntelliTest ile çalışmaya başlama](getting-started.md)**
  - [Önemli öznitelikler](getting-started.md#important-attributes)
  - [Önemli statik yardımcı sınıfları](getting-started.md#helper-classes)

* **[Test üretimi](test-generation.md)**
  - [Test oluşturucuları](test-generation.md#test-generators)
  - [Parametreli birim testi](test-generation.md#parameterized-unit-testing)
  - [Genel parametreli birim testi](test-generation.md#generic-parameterized)
  - [Özel durumlara izin verme](test-generation.md#allowing-exceptions)
  - [İç türleri test etme](test-generation.md#internal-types)
  - [Varsayımlar ve Onaylamalar](test-generation.md#assumptions-and-assertions)
  - [Koşul](test-generation.md#precondition)
  - [Mediğine](test-generation.md#postcondition)
  - [Test arızaları](test-generation.md#test-failures)
  - [Kurulum ve koparma](test-generation.md#setup-teardown)
  - [Daha fazla okuma](test-generation.md#further-reading)

* **[Giriş oluşturma](input-generation.md)**
  - [Kısıtlama çözücü](input-generation.md#constraint-solver)
  - [Dinamik kod kapsamı](input-generation.md#dynamic-code-coverage)
  - [Tamsayılar ve float](input-generation.md#integers-and-floats)
  - [Nesneler](input-generation.md#objects)
  - [Mevcut sınıfları örnekleme](input-generation.md#existing-classes)
  - [Görünürlük](input-generation.md#visibility)
  - [Parametreli hareketler](input-generation.md#parameterized-mocks)
  - [Yapılar](input-generation.md#structs)
  - [Diziler ve dizeler](input-generation.md#arrays-and-strings)
  - [Ek girişler alma](input-generation.md#additional-inputs)
  - [Daha fazla okuma](input-generation.md#further-reading)

* **[Keşif sınırları](exploration-bounds.md)**
  - [MaxConstraintSolverTime](exploration-bounds.md#maxconstraintsolvertime)
  - [MaxConstraintSolverMemory](exploration-bounds.md#maxconstraintsolvermemory)
  - [MaxBranches](exploration-bounds.md#maxbranches)
  - [Maxçağrılarında](exploration-bounds.md#maxcalls)
  - [MaxStack](exploration-bounds.md#maxstack)
  - [MaxConditions](exploration-bounds.md#maxconditions)
  - [Maxçalıştırmaları](exploration-bounds.md#maxruns)
  - [MaxRunsWithoutNewTests](exploration-bounds.md#maxrunswithoutnewtests)
  - [MaxRunsWithUniquePaths](exploration-bounds.md#maxrunswithuniquepaths)
  - [MaxExceptions](exploration-bounds.md#maxexceptions)
  - [Testexcludepathboundsexcebaşında](exploration-bounds.md#testexcludepathboundsexceeded)
  - [TestEmissionFilter](exploration-bounds.md#testemissionfilter)
  - [TestEmissionBranchHits](exploration-bounds.md#testemissionbranchhits)

* **[Öznitelik sözlüğü](attribute-glossary.md)**
  - [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull)
  - [PexClass](attribute-glossary.md#pexclass)
  - [PexGenericArguments](attribute-glossary.md#pexgenericarguments)
  - [PexMethod](attribute-glossary.md#pexmethod)
  - [Pexaraştırması Ationattributebase](attribute-glossary.md#pexexplorationattributebase)
  - [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
  - [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest)
  - [PexInstrumentAssemblyAttribute](attribute-glossary.md#pexinstrumentassemblyattribute)
  - [PexUseType](attribute-glossary.md#pexusetype)
  - [PexAllowedException](attribute-glossary.md#pexallowedexception)
  - [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly)
  - [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype)
  - [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest)

* **[Ayarlar şelale](settings-waterfall.md)**

* **[Statik yardımcı sınıfları](static-helper-classes.md)**
  - [Pexvarsay](static-helper-classes.md#pexassume)
  - [Pexonaylama](static-helper-classes.md#pexassert)
  - [PexChoose](static-helper-classes.md#pexchoose)
  - [PexObserve](static-helper-classes.md#pexobserve)
  - [Pexsembolicvalue](static-helper-classes.md#pexsymbolicvalue)

* **[Uyarılar ve hatalar](warnings-and-errors.md)**
  - [MaxBranches sayısı aşıldı](warnings-and-errors.md#maxbranches-exceeded)
  - [MaxConstraintSolverTime aşıldı](warnings-and-errors.md#maxconstraintsolvertime-exceeded)
  - [MaxConditions aşıldı](warnings-and-errors.md#maxconditions-exceeded)
  - [Maxçağrılarının sayısı aşıldı](warnings-and-errors.md#maxcalls-exceeded)
  - [MaxStack aşıldı](warnings-and-errors.md#maxstack-exceeded)
  - [Maxçalıştırmaları aşıldı](warnings-and-errors.md#maxruns-exceeded)
  - [MaxRunsWithoutNewTests aşıldı](warnings-and-errors.md#maxrunswithoutnewtests-exceeded)
  - [Çözüm değiştirilemez](warnings-and-errors.md#cannot-concretize-solution)
  - [Nesne oluşturmak için yardım gerekiyor](warnings-and-errors.md#help-construct)
  - [Türleri bulmak için yardım gerekiyor](warnings-and-errors.md#help-types)
  - [Kullanılabilir tür tahmin edildi](warnings-and-errors.md#usable-type-guessed)
  - [Araştırma sırasında beklenmeyen hata oluştu](warnings-and-errors.md#unexpected-exploration)
  - [TargetInvocationException](warnings-and-errors.md#targetinvocationexception)
  - [Açıklanmeyen yöntem çağrıldı](warnings-and-errors.md#uninstrumented-method-called)
  - [Dış yöntem çağrıldı](warnings-and-errors.md#external-method-called)
  - [Unınstrumentable yöntemi çağrıldı](warnings-and-errors.md#uninstrumentable-method-called)
  - [Test edilebilirlik sorunu](warnings-and-errors.md#testability-issue)
  - [Sınırlama](warnings-and-errors.md#limitation)
  - [Gözlemlenen çağrı uyumsuzluğu](warnings-and-errors.md#observed-call-mismatch)
  - [Statik alanda depolanan değer](warnings-and-errors.md#value-static-field)

## <a name="got-feedback"></a>Geri bildirim alındı mı?

Fikirlerinizi ve özellik isteklerinizi [Geliştirici topluluğu](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)' na gönderin.