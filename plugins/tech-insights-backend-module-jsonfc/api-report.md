## API Report File for "@backstage/plugin-tech-insights-backend-module-jsonfc"

> Do not edit this file. It is a report generated by [API Extractor](https://api-extractor.com/).

```ts
import { BooleanCheckResult } from '@backstage/plugin-tech-insights-common';
import { CheckResponse } from '@backstage/plugin-tech-insights-common';
import { CheckValidationResponse } from '@backstage/plugin-tech-insights-node';
import { FactChecker } from '@backstage/plugin-tech-insights-node';
import { Logger as Logger_2 } from 'winston';
import { Operator } from 'json-rules-engine';
import { TechInsightCheck } from '@backstage/plugin-tech-insights-node';
import { TechInsightCheckRegistry } from '@backstage/plugin-tech-insights-node';
import { TechInsightsStore } from '@backstage/plugin-tech-insights-node';
import { TopLevelCondition } from 'json-rules-engine';

// @public (undocumented)
export type CheckCondition = {
  operator: string;
  fact: string;
  factValue: any;
  factResult: any;
  result: boolean;
};

// @public (undocumented)
export const JSON_RULE_ENGINE_CHECK_TYPE = 'json-rules-engine';

// @public (undocumented)
export interface JsonRuleBooleanCheckResult extends BooleanCheckResult {
  // (undocumented)
  check: JsonRuleCheckResponse;
}

// @public (undocumented)
export interface JsonRuleCheckResponse extends CheckResponse {
  // (undocumented)
  rule: {
    conditions: ResponseTopLevelCondition & {
      priority: number;
    };
  };
}

// @public
export class JsonRulesEngineFactChecker
  implements FactChecker<TechInsightJsonRuleCheck, JsonRuleBooleanCheckResult>
{
  constructor({
    checks,
    repository,
    logger,
    checkRegistry,
    operators,
  }: JsonRulesEngineFactCheckerOptions);
  // (undocumented)
  getChecks(): Promise<TechInsightJsonRuleCheck[]>;
  // (undocumented)
  runChecks(
    entity: string,
    checks?: string[],
  ): Promise<JsonRuleBooleanCheckResult[]>;
  // (undocumented)
  validate(check: TechInsightJsonRuleCheck): Promise<CheckValidationResponse>;
}

// @public
export class JsonRulesEngineFactCheckerFactory {
  constructor({
    checks,
    logger,
    checkRegistry,
    operators,
  }: JsonRulesEngineFactCheckerFactoryOptions);
  // (undocumented)
  construct(repository: TechInsightsStore): JsonRulesEngineFactChecker;
}

// @public
export type JsonRulesEngineFactCheckerFactoryOptions = {
  checks: TechInsightJsonRuleCheck[];
  logger: Logger_2;
  checkRegistry?: TechInsightCheckRegistry<TechInsightJsonRuleCheck>;
  operators?: Operator[];
};

// @public
export type JsonRulesEngineFactCheckerOptions = {
  checks: TechInsightJsonRuleCheck[];
  repository: TechInsightsStore;
  logger: Logger_2;
  checkRegistry?: TechInsightCheckRegistry<any>;
  operators?: Operator[];
};

// @public (undocumented)
export type ResponseTopLevelCondition =
  | {
      all: CheckCondition[];
    }
  | {
      any: CheckCondition[];
    };

// @public (undocumented)
export type Rule = {
  conditions: TopLevelCondition;
  name?: string;
  priority?: number;
};

// @public (undocumented)
export interface TechInsightJsonRuleCheck extends TechInsightCheck {
  // (undocumented)
  rule: Rule;
}

// (No @packageDocumentation comment for this package)
```