#### Queriable Simple Example SPARQL:
[click me to try on fuseki](http://gaiadev01.isi.edu:3030/dataset.html?tab=query&ds=/clusters#query=PREFIX+aida%3A+%3Chttp%3A%2F%2Fdarpa.mil%2Faida%2FinterchangeOntology%23%3E%0APREFIX+skos%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0APREFIX+aidas%3A+%3Chttp%3A%2F%2Fdarpa.mil%2Fontologies%2FSeedlingOntology%23%3E%0A%0ACONSTRUCT+%7B%0A++%3Fcrash_event+aidas%3Aconflict_attack_target+%3Ftarget+.%0A++%3Fcrash_event+aidas%3Aconflict_attack_attacker+%3Fattacker+.%0A%7D%0A%0A%23select+%3Fa+%3Fb+%3Fc+%3Fd%0AWHERE+%7B%0A++%3Fcrash_event+aidas%3Aconflict_attack_target+%3Ftarget+.%0A++%3Fcrash_event+aidas%3Aconflict_attack_attacker+%3Fattacker+.%0A%0A++%23+%3Cstring_entrypoint%3E%0A++%7B%0A++++%3Ftarget+skos%3AprefLabel+%22Mezhigorie%22+%3B%0A++++++++++++a+aida%3AEntity+.%0A++%7D%0A++UNION%0A++%23+%3Ctext_entrypoint%3E%0A++%7B%0A++++%3Ftarget+a+aida%3AEntity+%3B%0A++++++++++++aida%3AjustifiedBy+%3Fjustify+.%0A++++%3Fjustify+a+aida%3ATextJustification+.%0A++++%3Fjustify+aida%3Asource+%22HC00000DW%22+%3B%0A+++++++++++++aida%3AstartOffset+169+%3B%0A+++++++++++++aida%3AendOffsetInclusive+185+.%0A++%7D%0A%7D)
```
PREFIX aida: <http://darpa.mil/aida/interchangeOntology#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX aidas: <http://darpa.mil/ontologies/SeedlingOntology#>

CONSTRUCT {
  ?crash_event aidas:conflict_attack_target ?target .
  ?crash_event aidas:conflict_attack_attacker ?attacker .
}

WHERE {
  ?crash_event aidas:conflict_attack_target ?target .
  ?crash_event aidas:conflict_attack_attacker ?attacker .

  # <string_entrypoint>
  {
    ?target skos:prefLabel "Mezhigorie" ;
            a aida:Entity .
  }
  UNION
  # <text_entrypoint>
  {
    ?target a aida:Entity ;
            aida:justifiedBy ?justify .
    ?justify a aida:TextJustification .
    ?justify aida:source "HC00000DW" ;
             aida:startOffset 169 ;
             aida:endOffsetInclusive 185 .
  }
}
```

#### Example XML:
```
<?xml version="1.0"?>
<query id="AIDA_M09_TA2_Q2">
    <graph>
        <edges>
            <edge id="AIDA_M09_TA2_Q2_1">
                <subject> ?crash_event </subject>
                <predicate> Conflict.Attack_Target </predicate>
                <object> ?target </object>
            </edge>
            <edge id="AIDA_M09_TA2_Q2_2">
                <subject> ?crash_event </subject>
                <predicate> Conflict.Attack_Agent </predicate>
                <object> ?agent </object>
            </edge>
            <edge id="AIDA_M09_TA2_Q2_3">
                <subject> ?affiliation_relation </subject>
                <predicate> GeneralAffiliation.APORA_Affiliate </predicate>
                <object> ?agent </object>
            </edge>
            <edge id="AIDA_M09_TA2_Q2_4">
                <subject> ?affiliation_relation </subject>
                <predicate> GeneralAffiliation.APORA_Affiliation </predicate>
                <object> ?affliation </object>
            </edge>
        </edges>
    </graph>
    <entrypoints>
        <string_entrypoint>
            <node> ?target </node>
            <name_string> MH-17 </name_string>
            <enttype> Vehicle </enttype>
        </string_entrypoint>
        <text_entrypoint>
            <node> ?target </node>
            <doceid> HC000T6CQ </doceid>
            <start> 100 </start>
            <end> 104 </end>
            <enttype> Vehicle </enttype>
        </text_entrypoint>
        <video_entrypoint>
            <node> ?target </node>
            <doceid> IC0019NAK </doceid>
            <keyframeid> IC0019NAK_101 </keyframeid>
            <topleft> 20,20 </topleft>
            <bottomright> 50,50 </bottomright>
            <enttype> Vehicle </enttype>
        </video_entrypoint>
        <image_entrypoint>
            <node> ?target </node>
            <doceid> IC0011TFO </doceid>
            <topleft> 20,20 </topleft>
            <bottomright> 50,50 </bottomright>
            <enttype> Vehicle </enttype>
        </image_entrypoint>
<!--
        <audio_entrypoint>
            <node> ?target </node>
            <doceid> HC000ZKCG </doceid>
            <segmentid> HC000ZKCG_210 </segmentid>
            <start> 20,20 </start>
            <end> 50,50 </end>
            <enttype> Vehicle </enttype>
        </audio_entrypoint>
-->
    </entrypoints>
</query>

```

#### Converted to SPARQL:
Did not find corresponding ontology of `<segmentid>` .
```
PREFIX aida: <http://darpa.mil/aida/interchangeOntology#>
PREFIX xij: <http://isi.edu/xij-rule-set#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX aidas: <http://darpa.mil/ontologies/SeedlingOntology#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX schema: <http://schema.org/>
PREFIX ldcOnt: <https://tac.nist.gov/tracks/SM-KBP/2018/ontologies/SeedlingOntology#>
PREFIX olia:  <http://purl.org/olia/system.owl#>
PREFIX aidaDomainCommon: <https://tac.nist.gov/tracks/SM-KBP/2018/ontologies/AidaDomainOntologiesCommon#>
PREFIX owl:   <http://www.w3.org/2002/07/owl#>
PREFIX rdfs:  <http://www.w3.org/2000/01/rdf-schema#>
PREFIX ldc:   <https://tac.nist.gov/tracks/SM-KBP/2018/ontologies/LdcAnnotations#>

CONSTRUCT {
  ?crash_event ldcOnt:Conflict.Attack_Target ?target .
  ?crash_event ldcOnt:Conflict.Attack_Attacker ?attacker .
  ?affiliation_relation ldcOnt:GeneralAffiliation.APORA_Affiliate ?attacker .
  ?affiliation_relation ldcOnt:GeneralAffiliation.APORA_Affiliation ?affliation .
}
WHERE {
  ?crash_event ldcOnt:Conflict.Attack_Target ?target .
  ?crash_event ldcOnt:Conflict.Attack_Attacker ?attacker .
  ?affiliation_relation ldcOnt:GeneralAffiliation.APORA_Affiliate ?attacker .
  ?affiliation_relation ldcOnt:GeneralAffiliation.APORA_Affiliation ?affliation .

  # <string_entrypoint>
  {
    ?target skos:prefLabel "MH-17" ;
            a ldcOnt:Vehicle .
  }
  UNION
  # <text_entrypoint>
  {
    ?target a ldcOnt:Vehicle ;
            aida:justifiedBy ?justify .
    ?justify a aida:TextJustification .
    ?justify aida:source "HC000T6CQ" ;
             aida:startOffset 100 ;
             aida:endOffsetInclusive 104 .
  }
  UNION
  # <video_entrypoint>
  {
    ?target a ldcOnt:Vehicle ;
            aida:justifiedBy ?justify .
            ?justify a aida:KeyFrameJustification .
            ?justify aida:source "HC000T6CQ" ;
                     aida:keyFrame "IC0019NAK_101" ;
                     aida:BoundingBoxPropertyShape ?boundingBox .
                     ?boundingBox aida:boundingBoxUpperLeftX 20 ;
                                  aida:boundingBoxUpperLeftY 20 ;
                                  aida:boundingBoxLowerRightX 50 ;
                                  aida:boundingBoxLowerRightY 50 .
  }
  UNION
  # <image_entrypoint>
  {
    ?target a ldcOnt:Vehicle ;
            aida:justifiedBy ?justify .
            ?justify a aida:ImageJustification .
            ?justify aida:source "HC000T6CQ" ;
                     aida:BoundingBoxPropertyShape ?boundingBox .
                     ?boundingBox aida:boundingBoxUpperLeftX 20 ;
                                  aida:boundingBoxUpperLeftY 20 ;
                                  aida:boundingBoxLowerRightX 50 ;
                                  aida:boundingBoxLowerRightY 50 .
  }
  UNION
  # <audio_entrypoint>
  {
    ?target a ldcOnt:Vehicle ;
            aida:justifiedBy ?justify .
            ?justify a aida:AudioJustification .
            ?justify aida:source "HC000T6CQ" ;
                     <segmentid> "HC000ZKCG_210" ;
                     aida:startTimestamp 1.2 ;
                     aida:endTimestamp 2.1 .
  }
}
```
