# Команды для консоли браузера

## 1. Получить список всех вопросов (titles + URLs)

Открой страницу: https://it-incubator.io/prosobesim/react-frontend/roadmap?s=3E0D7B

```js
const items = document.querySelectorAll('a.block');
const data = [...items].map((a, i) => ({
  id: i + 1,
  title: a.querySelector('.text-sm.font-medium.truncate')?.textContent?.trim(),
  category: a.querySelector('.text-xs.text-muted-foreground')?.textContent?.trim() || '',
  url: a.href
}));
console.log(JSON.stringify(data, null, 2));
copy(JSON.stringify(data, null, 2));
console.log(`Скопировано ${data.length} вопросов в буфер обмена!`);
```

## 2. Скачать контент всех 112 вопросов

Открой любую страницу на it-incubator.io, затем вставь в консоль:

```js
(async () => {
  const urls = [
    "https://it-incubator.io/prosobesim/react-frontend/question/browser-api/document-and-page-objects/browser-apis/alert-prompt-confirm",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/asynchronous-programming/event-loop/blocking-code",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es6/classes/default/basic-syntax",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/events/binding/how-not-to-lose-context",
    "https://it-incubator.io/prosobesim/react-frontend/question/software-development-processes/bug-tracking-systems/default/purpose-of-using-bug-trackers",
    "https://it-incubator.io/prosobesim/react-frontend/question/software-engineering-practices/algorithms-and-data-structures/default/algorithm-definition",
    "https://it-incubator.io/prosobesim/react-frontend/question/browser-api/html/default/adding-of-scripts",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/common/default/conditional-operators",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es6/common/default/array-at-method",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/jsx/fragments/purpose-of-react-fragments",
    "https://it-incubator.io/prosobesim/react-frontend/question/software-development-processes/version-control-system-git/default/basic-git-operations",
    "https://it-incubator.io/prosobesim/react-frontend/question/software-engineering-practices/network/cors/why-do-we-need-cors",
    "https://it-incubator.io/prosobesim/react-frontend/question/browser-api/storages/cookie/setting-and-getting-of-cookies",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/data-types/common/list-of-types",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es6/modules/default/import-export-as",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/optimization/basic-react-optimization/keys-usage-in-react",
    "https://it-incubator.io/prosobesim/react-frontend/question/software-development-processes/version-control-system-git/default/branching-tagging-merging",
    "https://it-incubator.io/prosobesim/react-frontend/question/software-engineering-practices/network/rest/what-is-rest",
    "https://it-incubator.io/prosobesim/react-frontend/question/browser-api/document-and-page-objects/events/basic-types-of-dom-events",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/functions/common/immediately-invoked-function-expressions",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es6/network/fetch/basic-usage-fetch",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/reconciliation/fiber/explain-fiber-algorithm",
    "https://it-incubator.io/prosobesim/react-frontend/question/software-development-processes/version-control-system-git/default/group-work-and-vcs-concepts",
    "https://it-incubator.io/prosobesim/react-frontend/question/software-engineering-practices/algorithms-and-data-structures/default/basic-data-structures",
    "https://it-incubator.io/prosobesim/react-frontend/question/browser-api/storages/localstorage-sessionstorage/local-vs-session-storages",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/objects/common/for-in-cycles",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es6/asynchronous-programming/promise/exceptions-errors-handling",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/events/bubbling-event-in-react/component-bubbling-basics",
    "https://it-incubator.io/prosobesim/react-frontend/question/software-development-processes/version-control-system-git/default/pull-request-workflow",
    "https://it-incubator.io/prosobesim/react-frontend/question/browser-api/html/default/basic-scheme-for-html-document",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/prototypes-inheritance/default/chain-of-prototypes",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es6/classes/default/inheritance",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/jsx/jsxless-react/why-import-react-pre-v17",
    "https://it-incubator.io/prosobesim/react-frontend/question/browser-api/storages/cookie/what-is-cookie",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/regular-expressions/default/basic-regexp-pattern",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es6/common/default/arrow-functions-vs-plain",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/reconciliation/jobs/prioritization-basics",
    "https://it-incubator.io/prosobesim/react-frontend/question/browser-api/document-and-page-objects/events/dom-events-handling-add-remove-event-handlers",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/asynchronous-programming/scheduling/clear-timers-intervals",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es6/modules/default/import-export-syntax",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/redux/reducers/confident-writing-reducer",
    "https://it-incubator.io/prosobesim/react-frontend/question/browser-api/storages/localstorage-sessionstorage/storages-purpose",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/data-types/date-and-time/set-get-date",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es6/asynchronous-programming/promise/states-of-promises",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/components/functional-components/functional-components-basics",
    "https://it-incubator.io/prosobesim/react-frontend/question/browser-api/html/default/difference-between-block-and-inline-elements",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/functions/execution-context/global-context-window",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es6/classes/default/private-protected-properties-methods",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/events/controlled-uncontrolled-components/difference-controlled-uncontrolled",
    "https://it-incubator.io/prosobesim/react-frontend/question/browser-api/document-and-page-objects/events/ways-to-prevent-dom-event",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/common/default/hoisting",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es6/common/default/destructuring-spread-operator",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/reconciliation/recursion-on-child-elements/why-recursion-needed-child-components",
    "https://it-incubator.io/prosobesim/react-frontend/question/browser-api/html/default/element-visibility-ways-to-hide-element",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/functions/common/types-of-functions",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es6/modules/default/star-for-import",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/jsx/render/why-and-how-use-reactdom-library",
    "https://it-incubator.io/prosobesim/react-frontend/question/browser-api/html/default/fonts-adding",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/objects/common/set-get-delete-object-properties-methods",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es6/common/default/flat-flatmap-includes-array-from",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/redux/selectors/explain-selectors-own-words",
    "https://it-incubator.io/prosobesim/react-frontend/question/browser-api/html/default/frameworks-layout-technique",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/prototypes-inheritance/default/create-object-with-prototype",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es6/common/default/for-of-cycles",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/events/jsx-handlers/difference-native-vs-react-handlers",
    "https://it-incubator.io/prosobesim/react-frontend/question/browser-api/html/default/html-links-link-target",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/regular-expressions/default/global-case-insensitive-search",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es6/common/default/keys-values-entries-methods",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/routing/react-router/react-router-basics",
    "https://it-incubator.io/prosobesim/react-frontend/question/browser-api/html/default/html-symbols-usage",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/asynchronous-programming/scheduling/settimeout-setinterval",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es6/common/default/object-hasown",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/events/synthetic-event/what-is-synthetic-event",
    "https://it-incubator.io/prosobesim/react-frontend/question/browser-api/html/default/html-tables",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/functions/execution-context/this-definition",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es6/common/default/optional-mark-optional-chain",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/optimization/react-devtools-redux-devtools/devtools-usage-basics",
    "https://it-incubator.io/prosobesim/react-frontend/question/browser-api/html/default/margins-vs-paddings",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/common/default/if-condition",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es6/common/default/template-string",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/routing/react-router-api/api-components-basics",
    "https://it-incubator.io/prosobesim/react-frontend/question/browser-api/html/default/positioning",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/objects/common/set-get-object-keys",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es6/common/default/temporary-dead-zone",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/components/props/reverse-data-flow-to-parent",
    "https://it-incubator.io/prosobesim/react-frontend/question/browser-api/html/default/selectors-and-their-weight",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/prototypes-inheritance/default/get-and-set-object-prototype",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/events/working-with-forms/custom-forms-implementation",
    "https://it-incubator.io/prosobesim/react-frontend/question/browser-api/html/default/text-formatting-paragraphs",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/regular-expressions/default/two-methods-regexp-object",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/hooks/usestate-usereducer-usecontext/accepted-parameters",
    "https://it-incubator.io/prosobesim/react-frontend/question/browser-api/html/default/z-index",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/functions/execution-context/ways-to-bind-this",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/components/refs/what-is-ref-in-react",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/common/default/logical-operators",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/optimization/basic-react-optimization/shouldcomponentupdate-lifecycle-understanding",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/objects/common/ways-to-create-object",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/reconciliation/fiber/what-is-fiber",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/prototypes-inheritance/default/proto-and-prototype-properties",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/events/bubbling-event-in-react/working-with-bubbling-in-components",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/regular-expressions/default/two-ways-create-regexp",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/components/functional-components/state-in-functional-components",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/common/default/loops-while-for",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/events/controlled-uncontrolled-components/explain-essence-in-own-words",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/common/default/strict-vs-none-strict-comparison",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/components/props/understanding-props-purpose",
    "https://it-incubator.io/prosobesim/react-frontend/question/js-es5/common/default/switch-construction",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/hooks/usestate-usereducer-usecontext/explain-usestate-usereducer",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/components/refs/why-need-ref",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/events/controlled-uncontrolled-components/pros-cons-controlled-vs-uncontrolled",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/components/props/why-props-readonly",
    "https://it-incubator.io/prosobesim/react-frontend/question/react/hooks/usestate-usereducer-usecontext/work-with-basic-hooks"
  ];

  const results = [];
  const BATCH = 5;

  for (let i = 0; i < urls.length; i += BATCH) {
    const batch = urls.slice(i, i + BATCH);
    const fetched = await Promise.all(batch.map(async (url) => {
      try {
        const res = await fetch(url);
        const html = await res.text();
        const doc = new DOMParser().parseFromString(html, 'text/html');
        const main = doc.querySelector('main') || doc.querySelector('body');
        return { url, text: main?.innerText?.substring(0, 3000) || '' };
      } catch (e) {
        return { url, text: 'ERROR: ' + e.message };
      }
    }));
    results.push(...fetched);
    console.log(`Готово: ${results.length}/${urls.length}`);
  }

  const json = JSON.stringify(results, null, 2);
  const blob = new Blob([json], {type: 'application/json'});
  const a = document.createElement('a');
  a.href = URL.createObjectURL(blob);
  a.download = 'prosobesim-content.json';
  a.click();
  console.log('Файл скачан!');
})();
```

## 3. Отладка: посмотреть DOM-структуру элементов с определённым текстом

```js
document.querySelectorAll('[class]').forEach(el => {
  if (el.textContent.includes('ИСКОМЫЙ_ТЕКСТ')) {
    console.log(el.tagName, el.className, el.textContent.substring(0, 200));
  }
});
```
