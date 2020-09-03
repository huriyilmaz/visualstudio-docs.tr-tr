---
title: Microsoft. VisualStudio. TestTools. CppUnitTestFramework API 'SI
ms.date: 09/27/2019
ms.topic: reference
ms.author: corob
manager: jillfra
ms.workload:
- multiple
author: corob-msft
ms.openlocfilehash: 16ea629312237dd859e9eb1aad21b9b219de7229
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "82109435"
---
# <a name="microsoftvisualstudiotesttoolscppunittestframework-api-reference"></a>Microsoft. VisualStudio. TestTools. CppUnitTestFramework API başvurusu

Bu konu, ad alanının ortak üyelerini listeler `Microsoft::VisualStudio::CppUnitTestFramework` . Microsoft yerel birim testi çerçevesini temel alan C++ birim testlerini yazmak için bu API 'Leri kullanın. Konunun sonunda bir [kullanım örneği](#example) vardır.

Header ve lib dosyaları * \<Visual Studio installation folder> \VC\Auxiliary\VS\UnitTest*altında bulunur.

Üst bilgi ve LIB yolları yerel bir test projesinde otomatik olarak yapılandırılır.

## <a name="in-this-topic"></a><a name="In_this_topic"></a> Bu konuda

[CppUnitTest. h](#cppUnitTest_h)

- [Test sınıfları ve yöntemleri oluşturma](#create_test_classes_and_methods)

- [Başlatma ve Temizleme](#Initialize_and_cleanup)

  - [Test yöntemleri](#test_methods)

  - [Test sınıfları](#test_classes)

  - [Test modülleri](#test_modules)

- [Test öznitelikleri oluşturma](#create_test_attributes)

  - [Test yöntemi öznitelikleri](#test_method_attributes)

  - [Test sınıfı öznitelikleri](#test_class_attributes)

  - [Test modülü öznitelikleri](#test_module_attributes)

  - [Önceden tanımlanmış öznitelikler](#pre_defined_attributes)

    [CppUnitTestAssert. h](#cppUnitTestAssert_h)

  - [Genel onaylar](#general_asserts)

    - [Eşittir](#general_are_equal)

    - [Eşit değildir](#general_are_not_equal)

    - [Aynı](#general_are_same)

    - [Aynı değil](#general_are_not_same)

    - [Null](#general_is_null)

    - [Null değil](#general_is_not_null)

    - [Doğru](#general_is_True)

    - [Yanlış](#general_is_false)

    - [Başarısız](#general_Fail)

  - [Windows Çalışma Zamanı onayları](#winrt_asserts)

    - [Eşittir](#winrt_are_equal)

    - [Aynı](#winrt_are_same)

    - [Eşit değildir](#winrt_are_not_equal)

    - [Aynı değil](#winrt_are_not_same)

    - [Null](#winrt_is_null)

    - [Null değil](#winrt_is_not_null)

  - [Özel durum onayları](#exception_asserts)

    - [Özel durum bekliyor](#expect_exception)

      [Cppunittestgünlükçü. h](#cppunittestlogger_h)

    - [Medi](#logger)

    - [Ileti yaz](#write_message)

  - [Kullanım örneği](#example)

## <a name="cppunittesth"></a><a name="cppUnitTest_h"></a> CppUnitTest. h

### <a name="create-test-classes-and-methods"></a><a name="create_test_classes_and_methods"></a> Test sınıfları ve yöntemleri oluşturma

```cpp
TEST_CLASS(className)
```

Test yöntemleri içeren her sınıf için gereklidir. *ClassName* bir test sınıfı olarak tanımlar. `TEST_CLASS` ad alanı kapsamında bildirilmelidir.

```cpp
TEST_METHOD(methodName)
{
    // test method body
}
```

*MethodName* öğesini bir test yöntemi olarak tanımlar. `TEST_METHOD` , yöntemin sınıfının kapsamında bildirilmelidir.

### <a name="initialize-and-cleanup"></a><a name="Initialize_and_cleanup"></a> Başlatma ve Temizleme

#### <a name="test-methods"></a><a name="test_methods"></a> Test yöntemleri

```cpp
TEST_METHOD_INITIALIZE(methodName)
{
    // method initialization code
}
```

*MethodName* öğesini, her test yöntemi çalıştırılmadan önce çalışan bir yöntem olarak tanımlar. `TEST_METHOD_INITIALIZE` , bir test sınıfında yalnızca bir kez tanımlanabilir ve test sınıfının kapsamında tanımlanmalıdır.

```cpp
TEST_METHOD_CLEANUP(methodName)
{
    // test method cleanup  code
}
```

*MethodName* öğesini her test yöntemi çalıştırıldıktan sonra çalışan bir yöntem olarak tanımlar. `TEST_METHOD_CLEANUP` , bir test sınıfında yalnızca bir kez tanımlanabilir ve test sınıfının kapsamında tanımlanmalıdır.

#### <a name="test-classes"></a><a name="test_classes"></a> Test sınıfları

```cpp
TEST_CLASS_INITIALIZE(methodName)
{
    // test class initialization  code
}
```

*MethodName* öğesini, her test sınıfı oluşturulmadan önce çalışan bir yöntem olarak tanımlar. `TEST_CLASS_INITIALIZE` , bir test sınıfında yalnızca bir kez tanımlanabilir ve test sınıfının kapsamında tanımlanmalıdır.

```cpp
TEST_CLASS_CLEANUP(methodName)
{
    // test class cleanup  code
}
```

*MethodName* öğesini her test sınıfı oluşturulduktan sonra çalışan bir yöntem olarak tanımlar. `TEST_CLASS_CLEANUP` , bir test sınıfında yalnızca bir kez tanımlanabilir ve test sınıfının kapsamında tanımlanmalıdır.

#### <a name="test-modules"></a><a name="test_modules"></a> Test modülleri

```cpp
TEST_MODULE_INITIALIZE(methodName)
{
    // module initialization code
}
```

Bir modül yüklendiğinde çalıştırılan *MethodName* yöntemini tanımlar. `TEST_MODULE_INITIALIZE` , bir test modülünde yalnızca bir kez tanımlanabilir ve ad alanı kapsamında bildirilmelidir.

```cpp
TEST_MODULE_CLEANUP(methodName)
```

Bir modül kaldırıldığında çalıştırılan *MethodName* yöntemini tanımlar. `TEST_MODULE_CLEANUP` , bir test modülünde yalnızca bir kez tanımlanabilir ve ad alanı kapsamında bildirilmelidir.

### <a name="create-test-attributes"></a><a name="create_test_attributes"></a> Test öznitelikleri oluşturma

#### <a name="test-method-attributes"></a><a name="test_method_attributes"></a> Test yöntemi öznitelikleri

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_METHOD_ATTRIBUTE()
```

`TEST_METHOD_ATTRIBUTE` *Testmethodname*test yöntemine bir veya daha fazla makro ile tanımlanan öznitelikleri ekler.

`TEST_METHOD_ATTRIBUTE`Makro, *ÖznitelikAdı* ve *AttributeValue*değeri olan bir özniteliği tanımlar.

#### <a name="test-class-attributes"></a><a name="test_class_attributes"></a> Test sınıfı öznitelikleri

```cpp
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_CLASS_ATTRIBUTE()
```

`TEST_CLASS_ATTRIBUTE` *TestClassName*test sınıfına bir veya daha fazla makro ile tanımlanan öznitelikleri ekler.

`TEST_CLASS_ATTRIBUTE`Makro, *ÖznitelikAdı* ve *AttributeValue*değeri olan bir özniteliği tanımlar.

#### <a name="test-module-attributes"></a><a name="test_module_attributes"></a> Test modülü öznitelikleri

```cpp
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_MODULE_ATTRIBUTE()
```

`TEST_MODULE_ATTRIBUTE` *TestModuleName*test modülüne bir veya daha fazla makro ile tanımlanan öznitelikleri ekler.

`TEST_MODULE_ATTRIBUTE`Makro, *ÖznitelikAdı* ve *AttributeValue*değeri olan bir özniteliği tanımlar.

#### <a name="pre-defined-attributes"></a><a name="pre_defined_attributes"></a> Önceden tanımlanmış öznitelikler

Önceden tanımlanmış bu öznitelik makroları, yaygın durumlar için kolaylık olarak sağlanır. Yukarıda açıklanan makronun yerine kullanılabilir `TEST_METHOD_ATTRIBUTE` .

```cpp
TEST_OWNER(ownerAlias)
```

`TEST_METHOD_ATTRIBUTE` `Owner` *OwnerAlias*öğesinin Name ve Attribute değeri ile bir tanımlar.

```cpp
TEST_DESCRIPTION(description)
```

`TEST_METHOD_ATTRIBUTE` `Description` *Açıklaması ve açıklama*özniteliği değeri ile tanımlar.

```cpp
TEST_PRIORITY(priority)
```

`TEST_METHOD_ATTRIBUTE`Öncelik değeri ile bir adı `Priority` ve özniteliği tanımlar. *priority*

```cpp
TEST_WORKITEM(workitem)
```

Çalışma `TEST_METHOD_ATTRIBUTE` `WorkItem` öğesinin adı *workItem*ve öznitelik değeri ile bir tanımlar.

```cpp
TEST_IGNORE()
```

`TEST_METHOD_ATTRIBUTE`Adı `Ignore` ve özniteliği değeri ile bir tanımlar `true` .

## <a name="cppunittestasserth"></a><a name="cppUnitTestAssert_h"></a> CppUnitTestAssert. h

### <a name="general-asserts"></a><a name="general_asserts"></a> Genel onaylar

#### <a name="are-equal"></a><a name="general_are_equal"></a> Eşittir
İki nesnenin eşit olduğunu doğrulama

```cpp
template<typename T>
static void Assert::AreEqual(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

İki Double 'ın eşit olduğunu doğrulama

```cpp
static void Assert::AreEqual(
    double expected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

İki float 'ın eşit olduğunu doğrulama

```cpp
static void Assert::AreEqual(
    float expected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

İki Char * dizesinin eşit olduğunu doğrulama

```cpp
static void Assert::AreEqual(
    const char* expected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

İki w_char * dizesinin eşit olduğunu doğrulama

```cpp
static void Assert::AreEqual(
    const wchar_t* expected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-equal"></a><a name="general_are_not_equal"></a> Eşit değildir
İki Double Double 'ın eşit olmadığından emin olun

```cpp
static void Assert::AreNotEqual(
    double notExpected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

İki float 'ın eşit olmadığından emin olun

```cpp
static void Assert::AreNotEqual(
    float notExpected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

İki Char * dizesinin eşit olmadığından emin olun

```cpp
static void Assert::AreNotEqual(
    const char* notExpected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

İki w_char * dizesinin eşit olmadığından emin olun

```cpp
static void Assert::AreNotEqual(
    const wchar_t* notExpected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

İki başvuruyu işleç = = işlecine göre eşit değil olarak doğrulayın.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-same"></a><a name="general_are_same"></a> Aynı
İki başvuruyu aynı nesne örneğine (kimlik) başvurmuş olduğunu doğrulayın.

```cpp
template<typename T>
static void Assert::AreSame(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-same"></a><a name="general_are_not_same"></a> Aynı değil
İki başvuruların aynı nesne örneğine (kimlik) başvurmadığından emin olun.

```cpp
template<typename T>
static void Assert::AreNotSame (
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-null"></a><a name="general_is_null"></a> Null
Bir işaretçinin NULL olduğunu doğrulayın.

```cpp
template<typename T>
static void Assert::IsNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-not-null"></a><a name="general_is_not_null"></a> Null değil
Bir işaretçinin NULL olmadığından emin olun

```cpp
template<typename T>
static void Assert::IsNotNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-true"></a><a name="general_is_True"></a> Doğru
Koşulun doğru olduğunu doğrulama

```cpp
static void Assert::IsTrue(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-false"></a><a name="general_is_false"></a> Yanlış
Koşulun yanlış olduğunu doğrulama

```cpp
static void Assert::IsFalse(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="fail"></a><a name="general_Fail"></a> Neden
Test çalışması sonucunun başarısız olmasını zorla

```cpp
static void Assert::Fail(
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

### <a name="windows-runtime-asserts"></a><a name="winrt_asserts"></a> Windows Çalışma Zamanı onayları

#### <a name="are-equal"></a><a name="winrt_are_equal"></a> Eşittir
İki Windows Çalışma Zamanı işaretçilerinin eşit olduğunu doğrular.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

İki platform:: String ^ dizelerinin eşit olduğunu doğrular.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-same"></a><a name="winrt_are_same"></a> Aynı
İki Windows Çalışma Zamanı aynı nesneye başvuruda bulunduğunu doğrular.

```cpp
template<typename T>
static void Assert::AreSame(
    T% expected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-equal"></a><a name="winrt_are_not_equal"></a> Eşit değildir
İki Windows Çalışma Zamanı işaretçilerinin eşit olmadığını doğrular.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    T^ notExpected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

İki platform:: String ^ dizelerinin eşit olmadığını doğrular.

```cpp
static void Assert::AreNotEqual(
    Platform::String^ notExpected,
    Platform::String^ actual,
    bool ignoreCase = false,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-same"></a><a name="winrt_are_not_same"></a> Aynı değil
İki Windows Çalışma Zamanı başvurusunun aynı nesneye başvurmadığını doğrular.

```cpp
template<typename T>
static void Assert::AreNotSame(
    T% notExpected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-null"></a><a name="winrt_is_null"></a> Null
Windows Çalışma Zamanı işaretçisinin bir nullptr olduğunu doğrular.

```cpp
template<typename T>
static void Assert::IsNull(
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-not-null"></a><a name="winrt_is_not_null"></a> Null değil
Windows Çalışma Zamanı işaretçisinin bir nullptr olmadığını doğrular.

```cpp
template<typename T>
static void Assert::IsNotNull(
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

### <a name="exception-asserts"></a><a name="exception_asserts"></a> Özel durum onayları

#### <a name="expect-exception"></a><a name="expect_exception"></a> Özel durum bekliyor
Bir işlevin özel durum harekete geçirdiğini doğrulayın:

```cpp
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>
static void Assert::ExpectException(
    _FUNCTOR functor,
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo= NULL)
```

Bir işlevin özel durum harekete geçirdiğini doğrulayın:

```cpp
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>
    static void Assert::ExpectException(
    _RETURNTYPE (*func)(),
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo = NULL)
```

## <a name="cppunittestloggerh"></a><a name="cppunittestlogger_h"></a> Cppunittestgünlükçü. h

### <a name="logger"></a><a name="logger"></a> Medi
Günlükçü sınıfı, **Çıkış penceresi**yazılacak statik yöntemler içerir.

### <a name="write-message"></a><a name="write_message"></a> Ileti yaz
**Çıkış penceresi** bir dize yazın

```cpp
static void Logger::WriteMessage(const wchar_t* message)
```

```cpp
static void Logger::WriteMessage(const char* message)
```

## <a name="example"></a><a name="example"></a> Örneğinde
Bu kod, VSCppUnit kullanımının bir örneğidir. Öznitelik meta verileri, armatürler, onaylamaları olan birim testleri ve özel günlüğe kaydetme örneklerini içerir.

```cpp
// USAGE EXAMPLE

#include <CppUnitTest.h>

using namespace Microsoft::VisualStudio::CppUnitTestFramework;

BEGIN_TEST_MODULE_ATTRIBUTE()
    TEST_MODULE_ATTRIBUTE(L"Date", L"2010/6/12")
END_TEST_MODULE_ATTRIBUTE()

TEST_MODULE_INITIALIZE(ModuleInitialize)
{
    Logger::WriteMessage("In Module Initialize");
}

TEST_MODULE_CLEANUP(ModuleCleanup)
{
    Logger::WriteMessage("In Module Cleanup");
}

TEST_CLASS(Class1)
{

public:

    Class1()
    {
        Logger::WriteMessage("In Class1");
    }

    ~Class1()
    {
        Logger::WriteMessage("In ~Class1");
    }

    TEST_CLASS_INITIALIZE(ClassInitialize)
    {
        Logger::WriteMessage("In Class Initialize");
    }

    TEST_CLASS_CLEANUP(ClassCleanup)
    {
        Logger::WriteMessage("In Class Cleanup");
    }

    BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
        TEST_OWNER(L"OwnerName")
        TEST_PRIORITY(1)
    END_TEST_METHOD_ATTRIBUTE()

    TEST_METHOD(Method1)
    {
        Logger::WriteMessage("In Method1");
        Assert::AreEqual(0, 0);
    }

    TEST_METHOD(Method2)
    {
        Assert::Fail(L"Fail");
    }
};
```

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzun birim testi](../test/unit-test-your-code.md)
- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)
