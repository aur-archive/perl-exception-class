# Maintainer: Maxwell Pray a.k.a. Synthead <synthead@gmail.com>
# Contributor: Caleb Cushing <xenoterracide@gmail.com>

pkgname=perl-exception-class
_cpanname="Exception-Class"
pkgver=1.37
pkgrel=1
pkgdesc="A module that allows you to declare real exception classes in Perl"
arch=('any')
url="http://search.cpan.org/dist/$_cpanname"
license=('PerlArtistic' 'GPL')
depends=('perl>=5.5.0' 'perl-class-data-inheritable>=0.02' 'perl-devel-stacktrace>=1.20')
options=('!emptydirs')
source=("http://search.cpan.org/CPAN/authors/id/D/DR/DROLSKY/$_cpanname-$pkgver.tar.gz")
md5sums=('9953d120112d971f1deafdba9dc15aa7')

# Function to change to the working directory and set
# environment variables to override undesired options.
prepareEnvironment() {
	cd "$srcdir/$_cpanname-$pkgver"
	export \
		PERL_MM_USE_DEFAULT=1 \
		PERL_AUTOINSTALL=--skipdeps \
		PERL_MM_OPT="INSTALLDIRS=vendor DESTDIR='$pkgdir'" \
		PERL_MB_OPT="--installdirs vendor --destdir '$pkgdir'" \
		MODULEBUILDRC=/dev/null
}

build() {
	prepareEnvironment
	/usr/bin/perl Makefile.PL
	make
}

check() {
	prepareEnvironment
	make test
}

package() {
	prepareEnvironment
	make install

	# Remove "perllocal.pod" and ".packlist".
	find "$pkgdir" -name .packlist -o -name perllocal.pod -delete
}
