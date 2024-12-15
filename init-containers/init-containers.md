**Init Containers**
- These containers are used to run to *completion before the main pod starts up*.
- These can be used for;
    - If startup or setting up a pod requires different image.
    - To delay the startup to perform some health checks.
    - For security purposes, i.e, we want to access some external service but donot want to expose main container.
