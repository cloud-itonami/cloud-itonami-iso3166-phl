(ns statute.facts-test
  (:require [kotoba.lang.text :as str]
            [clojure.test :refer [deftest is]]
            [statute.facts :as facts]))

(deftest phl-has-spec-basis
  (let [sb (facts/spec-basis "PHL")]
    (is (= 2 (count sb)))
    (is (every? #(str/starts-with? (:statute/url %) "https://lawphil.net/") sb))
    (is (every? :statute/law-number sb))))

(deftest unknown-jurisdiction-has-no-spec-basis
  (is (nil? (facts/spec-basis "ATL")))
  (is (nil? (facts/spec-basis "ZZZ"))))

(deftest coverage-is-honest
  (let [c (facts/coverage ["PHL" "JPN" "ATL"])]
    (is (= 3 (:requested c)))
    (is (= 1 (:covered c)))
    (is (= ["ATL" "JPN"] (:missing-jurisdictions c)))))

(deftest by-topic-filters
  (is (= ["phl.ra-10173-data-privacy-act"]
         (mapv :statute/id (facts/by-topic "PHL" :privacy))))
  (is (empty? (facts/by-topic "PHL" :labor)))
  (is (empty? (facts/by-topic "ATL" :privacy))))
