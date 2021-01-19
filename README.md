Automatic Differentiation (AD) is a used to calculate the derivative of outputs of a model with respect to its inputs. Derivatives play a fundamental role in different areas of mathematics, statistics and engineering. For example, derivatives are needed to calculate:

* Gradients of objective functions used in optimization, parameter estimation and training of machine learning algorithms.
* Jacobian matrices required to solve stiff systems of differential equations.
* Local sensitivity of models to inputs.
* Uncertainty and error propagation through models.

In this repo, we focus on dual numbers as they are very easy and transparent to implement forward AD using C++. We create a new Dual datatype that automatically carries the derivative information. All we have to do is to implement dual arithmetic using overloading.


```cpp
template <typename Scalar>
class Dual
{
	public:
		typedef Scalar ScalarType;

		Dual(Scalar real = Scalar(), Scalar dual = Scalar());
		template <typename Scalar2>
			Dual(const Dual<Scalar2> &rhs);

		Scalar real() const;
		Scalar dual() const;

		Dual<Scalar> &operator=(Scalar rhs);
		Dual<Scalar> &operator+=(Scalar rhs);
		Dual<Scalar> &operator-=(Scalar rhs);
		Dual<Scalar> &operator*=(Scalar rhs);
		Dual<Scalar> &operator/=(Scalar rhs);

		template <typename Scalar2>
			Dual<Scalar> &operator=(const Dual<Scalar2> &rhs);
		template <typename Scalar2>
			Dual<Scalar> &operator+=(const Dual<Scalar2> &rhs);
		template <typename Scalar2>
			Dual<Scalar> &operator-=(const Dual<Scalar2> &rhs);
		template <typename Scalar2>
			Dual<Scalar> &operator*=(const Dual<Scalar2> &rhs);
		template <typename Scalar2>
			Dual<Scalar> &operator/=(const Dual<Scalar2> &rhs);

		Scalar mReal;
		Scalar mDual;

	private:
};
```

*Like other repos, this one is encrypted using git crypt. If you would like to collaborate please contact.*
