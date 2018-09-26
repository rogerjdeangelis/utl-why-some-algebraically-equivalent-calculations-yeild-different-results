# utl-why-some-algebraically-equivalent-calculations-yeild-different-results
Why some algebraically equivalent calculations yeild different results.

    Why some algebraically equivalent calculations yeild different results

    The change in the order of operations inside the cpu or the compiler can result in  a
    different result. The compiler and the CPU can decide on a different order
    of operations.

    Another reason for 128bit floats

    These algrebraically equivalent operations yeild different results

        sqrt(2)*1.01**8*constant("pi")/sqrt(3)
        (1/sqrt(3))*constant("pi")*1.01**8*sqrt(2)

        * Intel memory layout - not the same;
           =x===============================;
        A8=5BD346E498380640
        B8=5CD346E498380640

    data _null_;

     a=sqrt(2)*1.01**8*constant("pi")/sqrt(3);
     b=(1/sqrt(3))*constant("pi")*1.01**8*sqrt(2);

     * in memory layout;
     a8=put(a,rb8.);
     put a8= $hex16.;

     b8=put(b,rb8.);
     put b8= $hex16.;

     * reverse bits;
     put a= hex16.;
     put b= hex16.;

     * formatted;
     put a= e18.;
     put b= e18.;

    run;quit;


    * Intel memory layout;
       =x==============;
    A8=5BD346E498380640
    B8=5CD346E498380640

    * Intel reverse memory layout;
      ===============x
    A=40063898E446D35B
    B=40063898E446D35C

    A=2.77763536779E+00
    B=2.77763536779E+00
