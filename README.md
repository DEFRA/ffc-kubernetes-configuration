# FFC Kubernetes Configuration

Kubernetes configuration yaml files used in FFC clusters.

## Priority Classes

Priority classes help kubernetes understand which resources it would kill in the event that it's over utilized.

Without Priority classes a default value of 0 is given and they would be the first closed during preemption.

There are 3 Priority levels:
High (with a value of 1000)
Default (with a value of 600)
Low (with a value of 200)

## License

THIS INFORMATION IS LICENSED UNDER THE CONDITIONS OF THE OPEN GOVERNMENT LICENCE found at:

http://www.nationalarchives.gov.uk/doc/open-government-licence/version/3

The following attribution statement MUST be cited in your products and applications when using this information.

>Contains public sector information licensed under the Open Government license v3

### About the license
The Open Government Licence (OGL) was developed by the Controller of Her Majesty's Stationery Office (HMSO) to enable information providers in the public sector to license the use and re-use of their information under a common open licence.

It is designed to encourage use and re-use of information freely and flexibly, with only a few conditions.